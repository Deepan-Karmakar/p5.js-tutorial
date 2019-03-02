
PFont grand;
float t = 0;
float u = 0;
int x = 0;
int y = 0;
int z = 0;
float speed;
PImage img;
PImage imgtwo;
float s=0;
float w;
float time;
float osx;
float osy;
float theta;
float size =0;
float sizer=0;
float rando;
float m;
float phase;
float phasee;
float delay=0;
float flareon=0;
float jolteon=0;
float varry =1;
float varryable =1;
int doors=0;
int check =0;
float setoff=0;
static final int LINE_C =20;
static final int LINE_O =360;
float numb=0;
float er=0;
float umbreon=0;
float gen =0;
float open;
float fire;
float ball;
float checkpoint=0;
float meh;
int diag=0;
float corners=0;
int wave=int(random(10,20));
int lightning = 15;
int ning = 0;
int xx = 0;
int yy = 0;
//Freebie for next task is zz
int zz = 0;
int colorr;
float pick;
//Control of Wave Fluctuation from bottom of screen
float fluct=0;
int spacing;
int radius;
int form=int(random(4,10));
int text_spacing=560;
Bolt[] bolts = new Bolt[150];
void setup() {
 // background(255,150,240);
  size(1280,720);
 // img = loadImage("Texture1.jpg");
  img = loadImage("ERIKAPOEM.jpg");
  imgtwo = loadImage("ERIKAPOEMFLIP.jpg");
  for (int i = 0; i < stars.length; i++) {
    stars[i] = new Star(); 
  }
}

void draw() {
  fill(255,255,255,1);
  if(delay%2==0){
    quad(0,0,width,0,width,height,0,height);}
   delay=delay+.5;
   //grand = loadFont("Cochin-BoldItalic-30.vlw");
   //textSize(1);
   //text_spacing = 480;
   // textFont(grand);
    textSize(19);
    int text_gap=20;
    fill(jolteon/12,jolteon/12,jolteon/12,255-jolteon/10);
    //Poem Lines
  //Erika's Side Panels
  
   noStroke();
   fill(255-jolteon,200,200,12);
   //quad(345,0,934,0,934,720,345,720);
   background(255,173,204,10);
   tint(255,173,204,212);
  image(img,-7,0,352,720);
   tint(255,173,204, 212);  // Display at half opacity
   image(imgtwo,934, 0,352,720);
  //tint(210,250,200, 40);
 
   translate(width/2,height/2);
   //STARS
    for (int i = 0; i < LINE_C; i = i +1){
    stroke(0,0,0,225);
    //noStroke();
    fill(mouseX/4+83,7,168+(i-10)*6,205);
    //triangle(w(u+i),z(u+i),w1(u+i),z1(u+i),15,15);
   ellipse(y(i-mouseX+delay)*2,z1(i*mouseY+delay)*2,x(i),x(i));
   // point(x(t+i), y(t+i));
    }
  
   translate(-width/2,-height/2);
  
   
   if(jolteon<250){
    if(flareon==0){
      jolteon = jolteon+.5;
    }
    else{
      if(jolteon==-250){
      flareon=0;}
      else{
      jolteon=jolteon-.5;}
    }
    }
    else{
      jolteon=jolteon-.5;
      flareon=1;
    }
    int red=0;
    int green=0;
    int blue=0;
   /*
    if(delay%160==0){
    rando =random(-100,100);
    m =random(-100,100);
    size = 1;
    //varry=3;
    varry = int(random(1,3));
    noStroke();
    if(jolteon>100){
    fill(220+jolteon/10,100,130+(m)/20,3);
    }
    else if(jolteon>0){
      fill(200+jolteon/15,110,110,3);
    }
    else{
      fill(250+jolteon/15,180,190,3);
    }
      
    quad(0,0,width,0,width,height,0,height);
    }
    strokeWeight(0.1);
    translate(width/2,height/2);
    stroke(jolteon+150,size+800,100-rando,0);
    fill(250-2*jolteon,50+jolteon,size,5);
    strokeWeight(.1);
    if(varry==1){
    ellipse(rando,m,size*9,size*9);
    }
    if(varry==2){
    triangle((rando),m-7*size,rando-11*size,m+7*size+7*size,rando+11*size,m+7*size+7*size);
    }
    if(varry==3){
    quad((rando)-(7*size),m-7*size,rando+(7*size)+(7*size),m-7*size,(rando+7*size)+(7*size),m+7*size+(7*size),rando-size*7,m+7*size+7*size);
    }
    if(delay%103==0){
      numb =random(-100,100);
      er =random(-100,100);
      varryable = int(random(1,3));
      sizer = 1;
    }
    stroke(jolteon-150,sizer-100,100+numb,0);
    fill(150+2*jolteon,80-jolteon-er,200-sizer,5);
    strokeWeight(.1);
    if(varryable==2){
    ellipse(numb,er,sizer*9,sizer*9);
    }
    if(varryable==3){
    triangle((numb),er-7*sizer,numb-11*sizer,er+7*sizer+7*sizer,numb+11*sizer,er+7*sizer+7*sizer);
    }
    if(varryable==1){
    quad((numb)-(7*sizer),er-7*sizer,numb+(7*sizer)+(7*sizer),er-7*sizer,(numb+7*sizer)+(7*sizer),er+7*sizer+(7*sizer),numb-sizer*7,er+7*sizer+7*sizer);
    }
    size=size+.7;
    sizer=sizer+.7;
    if(delay%380==0){
      check =1;
      umbreon=1;
      gen = random(0.1,3);
    }
    
    if(check==1){
    noStroke();
      fill(rando+200,230,numb+200,3);
      ellipse(v(umbreon)*3,2*jolteon,30+umbreon*5,30+umbreon*5);
      fill(250+jolteon,250,250-jolteon,3);
      if(gen<1){
      ellipse(y(umbreon)*2,-jolteon,5+umbreon*8,5+umbreon*8);
      }
      else if(gen<2){
        ellipse(-jolteon,y(umbreon)*2,5+umbreon*8,5+umbreon*8);
      }
      else{
        ellipse(x(umbreon),z(umbreon)*2,5+umbreon*5,5+umbreon*5);
      }
      umbreon=umbreon+1;
      if(umbreon==250){
        check=0;
      }
    }
    */
    translate(-width/2,-height/2);
    /*
    point(w(u),z(u));
    point(w1(u),z(u));*/
    //saveFrame("output/ERIKATEST_######.png");
    t = t +.5;
    u = u+.1;
}
float x(float t) {
 return sin(t/10)*100+sin(t/5)*random(45,50); 
}
float y(float t) {
 return cos(t/15) * 100; 
}  
float z(float t) {
 return sin(t*5) / 30; 
}  
float v(float t) {
 return sqrt((50*50)-(t*t)); 
}  
float vv(float t) {
 return cos((t*t))*220; 
}  
float xx(float t) {
 return sin((t*t))*220; 
}  
float w(float u) {
 return tan(u/10)*150; 
} 
float w1(float u) {
 return sin(u/10)*20; 
}
float z1(float u) {
 return cos(u/20) * 100; 
}