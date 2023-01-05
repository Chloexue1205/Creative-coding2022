# Creative-coding2022

void setup(){
  size(720,720);
  background(0);
}

void draw(){
  int d=12;
  int partX=width/3;
  int partY=height/3;
    
  for(int k=0;k<partX/10+1;k++){
    stroke(random(255),random(255),random(255));
   //diagonal
  
    line(0,0+d*k,2*partX+d*k,height);
    line(0+d*k,0,width,2*partX+d*k);
    line(width,0+d*k,partX-d*k,height);
    line(width-d*k,0,0,2*partY+d*k);
 //vertical&horizontal
    line(partX+d/2*k,0,2*partX-partX/2-d/2*k,height);
    line(2*partX-d/2*k,0,2*partX-partX/2+d/2*k,height);
    line(0,partY+d/2*k,width,2*partY-partY/2-d/2*k);
    line(0,2*partY-partY/2+d/2*k,width,2*partY-d/2*k);
    
  }
  //saveFrame("frames/lineOUTPUT-####.png");
   
}
