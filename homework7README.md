# Creative-coding2022
//homework7 
void setup(){
  size(500,500);
}
void draw(){
  background(242,103,140);
 int n=int(map(mouseY,0,width,3,8));
 
  for(int i=-2;i<3;i++){
    pushMatrix();
    translate(width/2,height*2/3);
    rotate(PI/n*i);
    branch(200,20,4);
    popMatrix();
  }
  saveFrame("frame-#####.png");
  
}
  

void branch(float lens,float radius,float t){
  float l=lens;
  float theta=map(mouseX,0,width,PI/4,PI/8);
  stroke(255);
  strokeWeight(t);
  line(0,0,0,-lens);
  noStroke();
  fill(random(0,255),random(255),random(255));
  ellipse(0,-lens,radius,radius);
  lens*=0.45;
  radius*=0.45;
  t*=0.5;
 
  for(int count=1;count<=6;count++){
 if(lens>5){
 translate(0,-l/7);
  pushMatrix();
  rotate(theta);
  branch(lens,radius,t);
  popMatrix();
  pushMatrix();
  rotate(-theta);
  branch(lens,radius,t);
  popMatrix();
  }
 lens*=0.95;
}
}
