# Creative-coding2022

void setup(){
  size(600,600);
  background(25);
  initiateData();
 }



void draw(){
}
void keyPressed(){
  if (key=='r'||key=='R'){
    background(25);
    initiateData();
    }
}

void initiateData(){
 for(int n=0;n<4;n++)
 {
   int A=int (random(width));
   int B=int (random(height));
   stroke(255,195,75);
      strokeWeight(6);
      line(A,random(height),A,random(height));
      stroke(60,185,132);
      strokeWeight(6);
      line(A,random(height),A,random(height));
      line(random(width),B,random(width),B);
      line(random(width),B,random(width),B);
      stroke(150,111,175);
      strokeWeight(6);
      line(A,random(height),A,random(height));
      line(random(width),B,random(width),B);
      stroke(48,90,209);
      strokeWeight(6);
      line(A,random(height),A,random(height));
      line(random(width),B,random(width),B);
 }
 
   for(int i=0;i<width;i=i+120){
    for(int j=0;j<height;j=j+120){
    //  fill(0,random(255),0);
    float W=random(10,150);
    float H=random(10,150);
    int M=int(random(i,i+120));
    int N=int(random(j,j+120));
    int X=M-M%10;
    int Y=N-N%10;
    
     
  if (W*H>10000&&W*H<=40000){
    //fill(255,230,126);
    fill(255,195,75);
  }
  if (W*H>5000&&W*H<=10000){
   // fill(234,54,47);
    fill(60,185,132);
  }
  if (W*H>2000&&W*H<=5000){
   // fill(234,54,47);
    fill(255,132,70);
  }
  if (W*H<=2000){
    //fill(47,89,234);
    fill(150,111,175);
  }
  
  noStroke();
   rect(X,Y,W,H);
  
  
    }
    int C=int (random(width));
    int D=int (random(height));
    stroke(255);
      strokeWeight(6);
      line(C,random(height),C,random(height));
      line(random(width),D,random(width),D);
  }
  noStroke();
  fill(255,87,31);
  ellipse(random(600),random(600),100,100);
  fill(48,90,209);
  rect(random(600),random(600),120,160);

saveFrame("frames/mdlaOUTPUT-####.png");
}
