# Creative-coding2022

ArrayList<Particle> particles;
int[] list;
int posX,posY;
PVector axis;
int count,max;
char A='D';
PFont font1;
PFont font2;
PFont font3;
PFont font4;
PFont font5;
PFont font6;
PFont font7;
PFont font8;
int display=1;

float rotatediv1=0;
float rotatediv2=0;
char letter;
String words=" ";
boolean choice1=false;
boolean choice2=false;
float rate=30;
float rate1=30;


  color color1=#2AF52B;
  color color2=#F5C92A;
  color color3=#F52A75;
  color color4=#882AF5;
  color color5=#8F8DFA;
  color color6=#5CF5FC;
  color color7=0;
  color color8=180;
  color color9=255;
  color rotatecolor1=255;
  color rotatecolor2=255;
  color bg=#38F061;
  color background=0;
  color a=color(255,193,215);
  color b=color(190,242,169);
  color c=lerpColor(a,b,0.4);
  color lettercolor=255;
  color lettercolor1=#FF4B81;
  color lettercolor2=#8B7EB2;
  color lettercolor3=#25227E;
  color lettercolor4=#186444;
  color lettercolor5=0;
  color lettercolor6=255;
  color subcolor=200;
  color numcolor=200;
  color circle=200;
  color lettercolor12=0;
  color stitle=255;
  
  color t1black=#40403F;
  color t1red=#FF885D;
  color t1blue=#4476FA;
  color textc=255;
  
  color t2green=#62F26C;
  color t2pink=#FA3A67;
  
  color t3white=#FAF4E8;
  color t3red=#D8532E;
  color t3green=#89B5BC;

color t4blue=#5461A0;
color t4blue2=#A4B3D6;

color t5red=#E33929;
color t5blue=#1959E0;
color t5green=#2EB76D;
color t5yellow=#FFDD31;
  
   
 
  boolean line=false;
  
  void setup(){
    font2=createFont("AlNile-Bold",20);
    font3=createFont("AlNile-Bold",350);
    font4=createFont("AlNile-Bold",13);
    font5=createFont("AlNile-Bold",100);
    font6=createFont("AlNile-Bold",20);
    font7=createFont("AlNile-Bold",45);
    font8=createFont("Avenir-Roman",12);
  
    font1=createFont("AlNile-Bold",500);
    colorMode(RGB,255,255,255);
    size(690,780);
    //frameRate(30);
    noStroke();
    fill(bg);
    count=0;
    max=140;
    textAlign(CENTER,CENTER);
    textFont(font1);
    textSize(500);
  
    text(A,250,400);
    //ellipse(50,50,20,20);
   // ellipse(90,50,20,20);
    
    list=new int[width*height];
    loadPixels();
    for(int y=0;y<=height-1;y++){
      for(int x=0;x<width-1;x++){
        color p=pixels[y*width+x];
       if(red(p)<57){
         list[y*width+x]=0;
       }
       else{
         list[y*width+x]=1;
       }
      }
    }
    updatePixels();
    
    particles=new ArrayList<Particle>();
     
    
  }
  
  void draw(){
    
  ellipseMode(CENTER);
    frameRate(rate);
    textFont(font2);
     if(choice1==false&&choice2==false){
       background(0);
       fill(247,217,107);
       rect(15,15,660,750);
       textAlign(CENTER,CENTER);
       
       textFont(font2);
       fill(255);
       textSize(80);
       text("Dynamic Poster",340,260);
       textSize(25);
       text("First,click the ellipse to choose the template",340,340);
       textSize(15);
       fill(0);
      text("You can also press ENTER to come back to the page again",340,370);
      noStroke();
      fill(255);
       rect(260,400,50,20);
       ellipse(260,410,20,20);
       ellipse(310,410,20,20);
       text("template 1",285,430);
       rect(370,400,50,20);
       ellipse(370,410,20,20);
       ellipse(420,410,20,20);
        text("template 2",395,430);
     }
       
     if (mousePressed&&mouseX<320&&mouseX>250&&mouseY<420&&mouseY>400){  
        choice1=true;
      }
     if( mousePressed&&mouseX<430&&mouseX>360&&mouseY<420&&mouseY>400){
       choice2=true;
     }
 
  if (choice1){  
    
    if(count<max){
      int i=0;
      while(i<5){
        axis=new PVector(int(random(80,width-100)),int(random(80,height-100)));
        if(list[int(axis.y*width+axis.x)]==0){
          particles.add(new Particle(axis.x,axis.y));
          i++;
          count++;
        }
      }
    }
    
    background(background);
    noStroke();
    fill(circle,180);
     ellipseMode(CENTER);
    ellipse(260,470,450,450);
    
    textFont(font3);
    textSize(350);
    fill(numcolor,120);
    for(int a=0;a<30;a=a+10){
    text("2",380,200+a);
    text("0",10,500+a);
    text("2",240,755+a);
    text("2",380,755+a);
     
    }
    if(a==30){
       a=0;
     }
     
    //control desk
    textFont(font4);
  textAlign(LEFT,LEFT);
    fill(230);
    rect(540,0,150,780);
    fill(0);
    textSize(13);
    text("grid",553,19);
    fill(0);
    rect(570,30,100,30);
    fill(255);
    text("show grid",585,50);
    fill(0);
    text("Framerate",553,260);
    text("Template Directiom",553,385);
     text("1.serious",570,405);
     text("2.fashinable",570,425);
     text("3.vintage",570,445);
     text("4.simple",570,465);
     text("5.childish",570,485);
     text("6.default",570,505);
      text("shape",553,320);
     ellipse(580,340,20,20);
     ellipse(620,340,20,20);
     ellipse(660,340,20,20);

    
    fill(255);
    rect(570,270,100,20);
    fill(0);
    rect(570,270,rate1,20);
    fill(255);
    //textSize(18);
    
    if(mousePressed&&mouseX<670&&mouseX>570&&mouseY>270&&mouseY<290){
      rate1=map(mouseX,570,670,0,100);
      rate=map(mouseX,570,670,20,60);
      
    }
    
    
  
  
    
  //subtitile text
    fill(0);
    textSize(13);
    text("enter the subtitle",553,90);
    fill(255);
    rect(570,100,100,30);
    fill(0);
    text(words,580,120); 
    
   //color template
    textSize(13);
    text("color template",553,160);
    ellipse(580,180,20,20);
    textSize(15);
    fill(255);
    textAlign(CENTER,CENTER);
    text("1",580,177);
    fill(0);
    ellipse(620,180,20,20);
    fill(255);
    text("2",620,177);
    fill(0);
    ellipse(660,180,20,20);
    fill(255);
    text("3",660,177);
    fill(0);
    ellipse(580,220,20,20);
    fill(255);
    text("4",580,217);
    fill(0);
    ellipse(620,220,20,20);
    fill(255);
    text("5",620,217);
    fill(0);
    ellipse(660,220,20,20);
    fill(255);
    text("6",660,217);
    
   
    
   
    
    
    
  
  //main subject
   
    for(int i=0;i<particles.size();i++){
      Particle p=particles.get(i);
      fill(255);
      noStroke();
      if(display==1){
      p.display(lettercolor,lettercolor12,0);
      p.update();
      }
       if(display==2){
      p.display3(lettercolor,lettercolor12,0);
      p.update();
      }
      if(display==3){
      p.display4(lettercolor,lettercolor12,0);
      p.update();
      }
    }
     
    /* for(int j=0;j<particles.size();j++){
      Particle p=particles.get(j);
      fill(255);
      noStroke();
      p.display2();
      p.update();
    }*/
    
   
    fill(255);
   // font2=createFont("AlNile-Bold",48);
    textFont(font2);
    textAlign(LEFT,LEFT);
    textFont(font6);
    textSize(20);
    fill(stitle);
    text("Shanghai JiaoTong University",20,180);
    textSize(45);
    textFont(font7);
   
    text("School Of Design ",20,150);

    fill(subcolor);
    
    textFont(font5);
    textSize(100);
    if(words==" "){
    text("TOPIC",20,100);
    }else{
      text(words,-3,100);
    }
    
    textSize(12);
    textFont(font8);
    fill(textc);
    text("Time&Date:   ",20,230);
    text("Place:MinHang",20,250);
    
    text("here:some",20,655);
    
    text("detalis of the",20,670);
    text("certain activity.",20,685);
    text("including the pur-",20,700);
    text("-pose and the aim,",20,715);
    text("descriptions and",20,730);
    text("other important or",20,745);
    text("fun facts",20,760);
    text("organizor:SJTU",150,730);
    text("supportor:   ",150,745);
    text("attender",150,760);
   
   
   
    
   
    //rotate text
    String word;
     if(words==" "){
   word="hi!this is the theme";
     }else{
       word=words;
     }
    for(int rcount=0;rcount<word.length();rcount++){
      pushMatrix();
      translate(width/2-80,height/2+80);
      rotate(TWO_PI/word.length()*rcount+rotatediv1);
      pushMatrix();
      translate(230,0);
      rotate(PI/2);
      fill(rotatecolor1);
      textSize(22);
      
      text(word.charAt(rcount),0,0);
     
      
      popMatrix();
      popMatrix();
    }
    rotatediv1+=0.01;
    
    
    String word2="School Of Design:SJTU";
    for(int rcount2=0;rcount2<word2.length()-1;rcount2++){
      pushMatrix();
      translate(width/2+110,320);
      rotate(TWO_PI/word2.length()*rcount2+rotatediv2);
      pushMatrix();
      translate(60,0);
      rotate(PI/2);
      fill(rotatecolor2);
      textSize(10);
      
      text(word2.charAt(rcount2),0,0);
     
      
      popMatrix();
      popMatrix();
    }
    rotatediv2+=0.01;
    
    
    
    //grim
   
    if(line){
      for(int lcount=0;lcount<4;lcount++){
        stroke(255);
        line(20+118*lcount+10*lcount,20,20+118*lcount+10*lcount,760);
        line(20+118*lcount+10*lcount+110,20,20+118*lcount+10*lcount+110,760);
      }
      for(int lcount2=0;lcount2<3;lcount2++){
        stroke(255);
        line(20,20+240*lcount2+20*lcount2,514,20+240*lcount2+20*lcount2);
        line(20,20+240*lcount2+20*lcount2+245,514,20+240*lcount2+20*lcount2+240);
        
    }
  }
  }
  
  
  
  
  
  
  if(choice2){
     if(count<max){
      int i=0;
      while(i<5){
        axis=new PVector(int(random(80,width-100)),int(random(80,height-100)));
        if(list[int(axis.y*width+axis.x)]==0){
          particles.add(new Particle(axis.x,axis.y));
          i++;
          count++;
        }
      }
    }
    
    background(background);
    noStroke();
    fill(circle,180);
    ellipse(260,300,450,450);
    
    textSize(350);
    textFont(font3);
    fill(numcolor,120);
    for(int a=0;a<30;a=a+10){
    text("2",10,200+a);
    text("0",380,320+a);
    text("2",10,550+a);
    text("2",380,650+a);
     
    }
    if(a==30){
       a=0;
     }
     
     textAlign(LEFT,LEFT);
    fill(230);
    rect(540,0,150,780);
    fill(0);
    textFont(font4);
    textSize(13);
    text("grid",553,19);
    fill(0);
    rect(570,30,100,30);
    fill(255);
    text("show grid",585,50);
    fill(0);
    text("Framerate",553,260);
     text("Template Directiom",553,385);
     text("1.serious",570,405);
     text("2.fashinable",570,425);
     text("3.vintage",570,445);
     text("4.simple",570,465);
     text("5.childish",570,485);
     text("6.default",570,505);
      text("shape",553,320);
     ellipse(580,340,20,20);
     ellipse(620,340,20,20);
     ellipse(660,340,20,20);

    fill(255);
    rect(570,270,100,20);
    fill(0);
    rect(570,270,rate1,20);
    fill(255);
    textSize(18);
    
    if(mousePressed&&mouseX<670&&mouseX>570&&mouseY>270&&mouseY<290){
      rate1=map(mouseX,570,670,0,100);
      rate=map(mouseX,570,670,20,60);
    }
  
    
  //subtitile text
    fill(0);
    textSize(13);
    text("enter the subtitle",553,90);
    fill(255);
    rect(570,100,100,30);
    fill(0);
    text(words,580,120); 
    
   //color template
    textSize(13);
    text("color template",553,160);
    ellipse(580,180,20,20);
    textSize(15);
    fill(255);
    textAlign(CENTER,CENTER);
    text("1",580,177);
    fill(0);
    ellipse(620,180,20,20);
    fill(255);
    text("2",620,177);
    fill(0);
    ellipse(660,180,20,20);
    fill(255);
    text("3",660,177);
    fill(0);
    ellipse(580,220,20,20);
    fill(255);
    text("4",580,217);
    fill(0);
    ellipse(620,220,20,20);
    fill(255);
    text("5",620,217);
    fill(0);
    ellipse(660,220,20,20);
    fill(255);
    text("6",660,217);
    
    
  
  //main subject
   
    for(int i=0;i<particles.size();i++){
      Particle p=particles.get(i);
      fill(255);
      noStroke();
     if(display==1){
      p.display(lettercolor,lettercolor12,-160);
      p.update();
      }
       if(display==2){
      p.display3(lettercolor,lettercolor12,-160);
      p.update();
      }
      if(display==3){
      p.display4(lettercolor,lettercolor12,-160);
      p.update();
      }
    }
    
    /* for(int j=0;j<particles.size();j++){
      Particle p=particles.get(j);
      fill(255);
      noStroke();
      p.display2();
      p.update();
    }*/
    
   
    fill(255);
    
   //textFont(font2);
    textAlign(LEFT,LEFT);
     textFont(font6);
    textSize(17);
    fill(stitle);
   text("ShangHai JiaoTong University",20,750);
    textSize(45);
    textFont(font7);
   
    text("School Of Design ",20,700);

    fill(subcolor);
    textFont(font5);
    textSize(100);
    if(words==" "){
    text("TOPIC",20,650);
    }else{
      text(words,-5,650);
    }
    
     textSize(12);
     textFont(font8);
    text("organizor:SJTU",290,735);
    text("supportor:   ",290,750);
    text("attender",290,765);
    
  
    text("FOR detalis of the",405,675);
    text("certain activity.",405,690);
    text("including the pur-",405,705);
    text("-pose and the aim,",405,720);
    text("descriptions and",405,735);
    text("other important or",405,750);
    text("fun facts",405,765);
   
   
    
   
    //rotate text
    String word;
     if(words==" "){
   word="hi!this is the theme";
     }else{
       word=words;
     }
    for(int rcount=0;rcount<word.length();rcount++){
      pushMatrix();
      translate(width/2-80,height/2-100);
      rotate(TWO_PI/word.length()*rcount+rotatediv1);
      pushMatrix();
      translate(240,0);
      rotate(PI/2);
      fill(rotatecolor1);
      textSize(22);
      
      text(word.charAt(rcount),0,0);
     
      
      popMatrix();
      popMatrix();
    }
    rotatediv1+=0.01;
    
    
    String word2="School Of Design:SJTU";
    for(int rcount2=0;rcount2<word2.length()-1;rcount2++){
      pushMatrix();
      translate(width/2+100,100);
      rotate(TWO_PI/word2.length()*rcount2+rotatediv2);
      pushMatrix();
      translate(60,0);
      rotate(PI/2);
      fill(rotatecolor2);
      textSize(10);
      
      text(word2.charAt(rcount2),0,0);
     
      
      popMatrix();
      popMatrix();
    }
    rotatediv2+=0.01;
    
    
    //grim
   
    if(line){
      for(int lcount=0;lcount<4;lcount++){
        stroke(255);
        strokeWeight(3);
        line(20+118*lcount+10*lcount,20,20+118*lcount+10*lcount,760);
        line(20+118*lcount+10*lcount+110,20,20+118*lcount+10*lcount+110,760);
      }
      for(int lcount2=0;lcount2<3;lcount2++){
        stroke(255);
          strokeWeight(3);
        line(20,20+240*lcount2+20*lcount2,514,20+240*lcount2+20*lcount2);
        line(20,20+240*lcount2+20*lcount2+245,514,20+240*lcount2+20*lcount2+240);
        
    }
  }
  }
    
    
  }
  
  
  
//input  
 
  void mouseClicked(){
    if(mouseX<670&&mouseX>570&&mouseY<60&&mouseY>30){
      line=!line;
    }
    
     if(mouseX<590&&mouseX>570&&mouseY<190&&mouseY>170){
    rotatecolor1=255;
    rotatecolor2=t1red;
    background=20;
    lettercolor=t1blue;
    subcolor=t1red;
    numcolor=255;
    textc=255;
    lettercolor12=20;
    stitle=255;
    circle=t1red;
    font5=createFont("AlNile-Bold",100);
    font6=createFont("AlNile-Bold",20);
    font7=createFont("AlNile-Bold",45);
  
  }
   if(mouseX<630&&mouseX>610&&mouseY<190&&mouseY>170){
    rotatecolor1=t2pink;
    rotatecolor2=0;
    background=255;
    lettercolor=t2pink;
    subcolor=0;
    numcolor=t2green;
    textc=0;
    lettercolor12=255;
    stitle=0;
    circle=180;
    font5=createFont("DamascusLight",100);
    font6=createFont("DamascusLight",20);
    font7=createFont("DamascusLight",45);
    
  }
   if(mouseX<670&&mouseX>650&&mouseY<190&&mouseY>170){
    rotatecolor1=0;
    rotatecolor2=0;
    background=t3white;
    lettercolor=t3red;
    subcolor=0;
    numcolor=t3red;
    textc=0;
    circle=t3green;
    lettercolor12=t3white;
    stitle=t3green;
    font5=createFont("Copperplate-Bold",100);
    font6=createFont("Didot-Bold",20);
    font7=createFont("Didot-Bold",45);
  
  }
  
  if(mouseX<590&&mouseX>570&&mouseY<230&&mouseY>210){
    rotatecolor1=t4blue;
    rotatecolor2=0;
    background=255;
    lettercolor=t4blue;
    subcolor=0;
    numcolor=t4blue2;
    textc=t4blue;
    lettercolor12=255;
    stitle=t4blue2;
    circle=220;
    font5=createFont("AlNile-Bold",100);
    font6=createFont("AlNile-Bold",20);
    font7=createFont("AlNile-Bold",45);
  
  }
   
  if(mouseX<630&&mouseX>610&&mouseY<230&&mouseY>210){
    rotatecolor1=t5green;
    rotatecolor2=t5red;
    background=255;
    lettercolor=t5red;
    subcolor=t5red;
    numcolor=t5yellow;
    textc=t5green;
    lettercolor12=255;
    stitle=t5green;
    circle=t5blue;
    font5=createFont("Chalkboard-Bold",100);
    font6=createFont("Chalkboard-Bold",20);
    font7=createFont("Chalkboard-Bold",45);
    
    
  }
  if(mouseX<670&&mouseX>650&&mouseY<230&&mouseY>210){
    rotatecolor1=255;
    rotatecolor2=255;
    background=0;
    lettercolor=255;
    subcolor=255;
    numcolor=255;
    textc=255;
    lettercolor12=0;
    stitle=255;
    circle=200;
    font5=createFont("AlNile-Bold",100);
    font6=createFont("AlNile-Bold",20);
    font7=createFont("AlNile-Bold",45);
  
    
  }
  if(mouseX<590&&mouseX>570&&mouseY<350&&mouseY>330){
    display=1;
  }
  if(mouseX<630&&mouseX>610&&mouseY<350&&mouseY>330){
    display=2;
    
  }
  if(mouseX<670&&mouseX>650&&mouseY<350&&mouseY>330){
    display=3;
  }
  }

  
  void keyTyped(){
    
     if (key>='0'&&key<='z'||key==' '){
      letter=key;
      words=words+letter;
      
  }
  if(key==ENTER){
   choice1=false;
   choice2=false;
     }
     
  }
  
  
  
  
  
  class Particle{
  PVector location;
  PVector velocity;
  float scale;
  int radius;
  color co;
  color co2;
  float difference;
  
  Particle(float x,float y){
    location=new PVector(x,y);
    velocity=new PVector(random(-2,2),random(0,1));
    scale=random(0.5,0.7);
    radius=int(scale*80*random(0,1.2));
  }
  
  void update(){
    location.add(velocity);
    if((list[int(location.y)*width+int(location.x+velocity.x)]==1)||(list[int(location.y)*width+int(location.x-velocity.x)]==1)){
      velocity.x*=-1;
    }
    if((list[int(location.y+velocity.y)*width+int(location.x)]==1)||(list[int(location.y-velocity.y)*width+int(location.x)]==1)){
      velocity.y*=-1;
    }
  }
  
  void display(color c,color c2,float di){
    co=c;
    co2=c2;
    difference=di;
    fill(co2);
    stroke(c);
    strokeWeight(2);
    ellipseMode(CORNER);
    ellipse(location.x,location.y+difference,radius,radius);
  }
   
   void display3(color c,color c2,float di){
    co=c;
    co2=c2;
    difference=di;
    fill(co2);
    stroke(c);
    strokeWeight(2);
    ellipseMode(CORNER);
    rect(location.x,location.y+difference,radius,radius);
  }
  
   void display4(color c,color c2,float di){
    co=c;
    co2=c2;
    difference=di;
    fill(co2);
    stroke(co2);
    strokeWeight(7);
    line(location.x+radius/2,location.y+difference,location.x,location.y+difference+radius);
  }
  
  void display2(){
    noStroke();
    fill(255);
    rect(location.x,location.y,radius-10,radius-10);
  }
}
  
