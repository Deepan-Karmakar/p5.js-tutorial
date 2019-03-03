  
Ripple Waves
by Marvin K	
   
  
OpenProcessing
My Sketches
My Feed

Edit Profile

Get Plus+ Membership

Sign out

Classes
Create a Class

View All Classes

Search
/ Recent s / Browse All physics game visualization particles color evolution circle lines
 Email info@openprocessing.org  Follow OpenProcessing on Twitter Twitter Credits Community Guidelines Terms of Service Privacy Policy 
windowResized()
1
with (p5) {
2
    let DIAMETER_X = 25;
3
    let DIAMETER_Y = 10;
4
​
5
    let NOISE_SCALE = 0.001;
6
​
7
    let T = 0;
8
    let T_D = 0.005;
9
​
10
    let CENTER_X;
11
    let CENTER_Y;
12
​
13
    let WAVE_SIZE = 200;
14
​
15
    function setup() {
16
        createCanvas(windowWidth, windowHeight);
17
​
18
        setVars();
19
​
20
        background(255);
21
        frameRate(30);
22
​
23
    }
24
    function +windowResized() {
25
        resizeCanvas(windowWidth, windowHeight);
26
        setVars();
27
​
28
    }
29
    function setVars() {
30
        CENTER_X = width / 2;
31
        CENTER_Y = height / 2;
32
    }
33
​
34
    function draw() {
35
​
36
        T += T_D;
37
​
38
        //background(255);
39
        noStroke();
40
        fill(255, 255, 255, 25);
41
​
42
        rect(0, 0, width, height);
43
        for (let x = -DIAMETER_X * 5; x < width + DIAMETER_X * 5; x += DIAMETER_X) {
44
            beginShape();
45
            for (let y = -DIAMETER_Y; y < height + DIAMETER_Y; y += DIAMETER_Y) {
46
​
47
​
48
                //noStroke();
Settings
Files
Reference
Engine  
v0.7.3
Text Size
LibrariesShow All
p5.dom
v0.7.2 (p5)
p5.sound
v0.7.2 (p5)
Console Keyboard Shortcuts
Join Plus+ for advanced code editor, no ads, custom libraries and more space.
 
