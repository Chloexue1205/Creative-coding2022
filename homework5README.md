# Creative-coding2022
nt t=100;
void setup(){
  size(800,800,P3D);

  
}
float a=1,b=1;
float shape(float theta,float m,float n,float n2,float n3){
  float t1=abs((1/a)*cos(m*theta/4));
  t1=pow(t1,n2);
   float t2=abs((1/b)*sin(m*theta/4));
   t2=pow(t2,n3);
   float t3=t1+t2;
  float r=pow(t3,-1/n);
    return r;
}

void draw(){
  background(0);
  noFill();
  stroke(255);
  float r=100;
  float c=255;
  float x1=2;
  float y1=2;
  float z1=2;
  textSize(20);
  text("s",15,44);
   text("c",15,74);
    text("x",15,104);
     text("y",15,134);
      text("z",15,164);
 rect(30,30,120,20);
  rect(30,60,120,20);
  rect(30,90,120,20);
  rect(30,120,120,20);
  rect(30,150,120,20);
  if(mouseX<150&&mouseX>30&&mouseY<50&&mouseY>30&&mousePressed){
   r=map(mouseX,30,110,50,400);
  
  }
  if(mouseX<150&&mouseX>30&&mouseY<80&&mouseY>60&&mousePressed){
   c=map(mouseX,30,110,255,0);
  }
   if(mouseX<150&&mouseX>30&&mouseY<110&&mouseY>90&&mousePressed){
   x1=map(mouseX,30,110,2,8);
   }
   if(mouseX<150&&mouseX>30&&mouseY<140&&mouseY>120&&mousePressed){
   y1=map(mouseX,30,110,2,8);
  
  }
  if(mouseX<150&&mouseX>30&&mouseY<170&&mouseY>150&&mousePressed){
   z1=map(mouseX,30,110,2,8);
  }
 
  
  fill(c);
  lights();
  translate(width/2,height/2);
  rotateX(map(mouseX,0,width,-PI,PI));
  rotateY(map(mouseY,0,height,-PI,PI));
  //sphere(200);
 
   beginShape(TRIANGLE_STRIP);
  for(int i=0;i<100;i++){
    
    float L=map(i,0,100,0,HALF_PI);
     float r1=shape(L,7,0.2,1.6,1.6);
    
   
    for (int j=0;j<100;j++){
     float H=map(j,0,100,0,PI);
     float r2=shape(H,10,0.6,1.6,1.6);
     float x=x1*r*r1*cos(L)*r2*cos(H);
      float y=y1*r*r1*sin(H)*r2*cos(L);
        float z=z1*r*r2*sin(H);
      
        stroke(c);
       vertex(x,y,z);
  
      
    }
   
    
  }
     endShape();
     saveFrame("frames-####.png");
    
}
    
