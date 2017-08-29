# p5.js WEBGL Mode Architecture

This document describes the structure of the p5.js WEBGL mode for p5.js contributors and maintainers—and any other interested parties.
If you're interested in using 3D graphics in your sketches, [view this tutorial](https://github.com/processing/p5.js/wiki/Getting-started-with-WebGL-in-p5) instead.

## Overview of Structure and Objects

The core objects in the WEBGL architecture are the p5.Renderer.GL, p5.Shader, p5.Texture, and p5.Geometry.
A single instance of p5.Renderer.GL manages its own p5.Shaders, p5.Textures, and p5.Geometry—a goal for this is to allow offscreen rendering using WebGL, but that hasn’t been tested yet.
Shaders and textures are associated with a specific GL context via the renderer.

### p5.RendererGL
The p5.RendererGL object is the renderer for WEBGL / 3D Mode in p5.js.
Derived from p5.Renderer, it provides additional functionality not available in 2D mode, such as: `box()`, `cone()`, use of shaders, accelerated texture rendering, and lighting.

* Manages—creates and caches—shaders (p5.Shader objects) and textures (p5.Texture objects)
* Prepares coordinates of shapes to be used as attribute arrays by shaders.
* Selects the correct shader for use when stroke, fill, texture, and various lighting methods are called, then supplies the appropriate uniforms to those shaders.
* Maintains data about lighting: a count of how many various types of lights are used and their parameters.
* Caches geometry for 3D primitives (in retained mode), with the exception of shapes created with begin/endShape, which are dynamically generated and pushed to GL every time one is drawn (in immediate mode).

The renderer manages choosing an appropriate p5.Shader for the current drawing conditions.

### p5.Shader
The p5.Shader class provides access to the uniforms and attributes of a GL program. 

* Compiles and links the vertex and fragment shader components
* Provides an API for accessing and setting shader attributes and uniforms
* Binds textures the shader needs before a shape is rendered
* Provides the bindShader() method for use in the render before a shape is drawn, then unbindShader() after the shape is drawn.

There are three default shaders, as documented in the Shader section.

### p5.Texture
The p5.Texture object manages GL state for a texture based on a `p5.Image`, `p5.MediaElement`, or `p5.Element`. In the future, this object could also be constructed for a piece of text to render in WEBGL mode.

* Internally handles processing image data based on type, so that the p5.Renderer implementation doesn’t have to make special exceptions in its own methods when handling textures
* Updates conditionally every frame by making a best guess at whether or not image data has changed. Tries not to upload the texture if no change has been made, to help performance.

### p5.Geometry
Shapes rendered in retain mode are stored as p5.Geometry objects in a cache in the p5.Renderer object. 
The renderer maps strings to p5.Geometry objects based on the shape drawn and its parameters (for example, geometry for a box created with `box(70, 80, 90, 10, 20)` is mapped from `'box|70|80|90|10|20’`).

* Stores vertices, normals, faces, and texture coordinates for the geometry primitives
* Provides methods for computing the faces and normals for a set of vertices

## Geometry: Retain and Immediate Mode
Retained geometry is used for 3D primitives, while immediate mode is used for shapes created with begin/endShape.

|Functions with retained geometry| Functions with immediate mode geometry | 2D functions not yet implemented|
|--------------------------------|----------------------------------------|---------------------------------|
|plane()                         | bezier()                               | arc()                           |
|box()                           | curve()                                | text()                          |
|sphere()                        | line()                                 | point()                         |
|cylinder()                      | beginShape()                           | curveVertex()                   |
|cone()                          | vertex()                               | bezierVertex()                  |
|ellipsoid()                     | endShape()                             | quadraticVertex()               |
|torus()                         |
|triangle()                      |
|ellipse()                       |
|rect()                          |
|quad()                          |






## Texture Management
A p5.Renderer.GL instances manages an array of p5.Textures objects on an as-needed basis.
Textures are created for images and videos used with the `texture()` method or as uniforms provided to custom shaders.

When the renderer needs a texture, it first checks if one has already been created for a given image/video, then provides that to a shader for rendering. A new texture is only created if an existing one cannot be found for the image/video.

## Shaders

### Types of Shaders

#### Color Shader
Provides flat shading of objects, based on the current fill color.

#### Light Shader (for lighting AND textures)
Accounts for:
* Lighting parameters set by `ambientLight()`, `directionalLight()`, and `pointLight()`
* Material parameters set by `ambientMaterial()`, and `specularMaterial()`
* Texture parameters, set by `texture()`

#### Normal Shader
The normal shader is set when `normalMaterial()` is in use. It uses the surface’s normal vector to determine a fragment color.


