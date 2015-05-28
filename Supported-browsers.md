## Our stated goal:

We support the current version of the browser, plus the previous major release of the browser.

## Potential issues:

* We are using webGL, which has limited support in IE 10, firefox, and the Android browser.
* We are using typed arrays, which does not have support for Uint8ClampedArray in IE 10 and IE Mobile 10/11.
* Canvas blend modes are not supported in IE.
* WebAudio is not supported in IE or the Android Browser.


As of May 2015, this means that we support:

|Browser            |  Current Version  | Previous Version|  Notes                    
|-------------------|------------------:|----------------:|--------------
|Internet Explorer  |             v. 11 |  v. 10          | Needs a polyfill for Uint8ClampedArray.  <br> No support for WebAudio. 
|IE Mobile          |             v. 11 |  v.10           | v.10 does not fully support webGL.<br>Needs a polyfill for Uint8ClampedArray.   <br> No support for WebAudio.
|Chrome             |             v. 43 |  v. 42          |
|Chrome for Android |             v. 40 |                 | Not sure if previous versions exist
|Firefox            |             v. 38 |  v. 37          | 
|Safari             |             v. 8  |  v. 7           |
|iOS Safari         |             v. 8.3|  v. 7.1         |
|Android Browser    |             v. 40 |  v. 4.4.4       | Does not support webGL.  <br> No support for WebAudio.

*We are not currently supporting Opera.*