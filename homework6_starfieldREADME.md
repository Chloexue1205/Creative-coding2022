# Creative-coding2022
//homework6

Star[] stars=new Star[800];
float theta;

void setup(){
  size(800,800);
  for(int i=0;i<stars.length;i++){
    stars[i]=new Star();
    
  }
}
void draw(){
  background(0);
  fill(255);
  // ellipse(30,30,10,10);
 // if((mouseX)*mouseX+(mouseY)*mouseY<=1300&&mousePressed){
    
 
  //}
  float theta=map(mouseY,0,height,0,height);
  translate(theta,theta);
  for(int i=0;i<stars.length;i++){
    stars[i].update();

    stars[i].show();
  }
  saveFrame("frame-#####.png");
}

class Star{
  float x;
  float y;
  float z;
  float pz;

  
 Star(){
   x=random(-width,width);
   y=random(-height,height);
   z=random(0,width);
   pz=z;
 }
 
 void update(){
   float t=map(mouseX,0,width,1,6);
   z=z-t;
   if(z<1){
     z=width;
   }
   
   
}
 void show(){
   fill(255);
   noStroke();
  
   float sx=map(x/z,0,1,0,width);
   float sy=map(y/z,0,1,0,width);
   float r=map(z,width,0,2,30);
   fill(random(0,255),random(0,255),random(0,255));
   ellipse(sx,sy,r,r);
   float psx=map(x/pz,0,1,0,width);
   float psy=map(y/pz,0,1,0,width);
   stroke(255);
   strokeWeight(0.3);
   line(psx,psy,sx,sy);
   
   
 }
}
