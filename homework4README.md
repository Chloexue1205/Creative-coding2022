# Creative-coding2022
to store some of my homework

PImage img;
int p=25;

void setup(){
   size(500,500);
   img=loadImage("sun2.jpg");
  background(255);
   smooth();
   frameRate(100);
}

void draw(){
   frameRate(100);
 int x=int(random(img.width));
 int y=int(random(img.height));
 int loc=x+y*img.width;
 
 loadPixels();
 float r=red(img.pixels[loc]);
 float g=green(img.pixels[loc]);
 float b=blue(img.pixels[loc]);
noStroke();
 fill(r,g,b,100);
 ellipse(x,y,p,p);
 
 /*saveFrame("frames/OUTPUT-####.png");*/
}
