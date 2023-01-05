# Creative-coding2022
//homework8 evolution
float mutationRate;
int totalPopulation = 150;
PFont font1;
 

DNA[] population;
ArrayList<DNA> matingPool;
String target;
 
void setup() {
  size(900, 300);
  font1=createFont("Phosphate-Solid",30);
 

  target = "2023,Happy New Year!";
  mutationRate = 0.005;
 

  population = new DNA[totalPopulation];
  for (int i = 0; i < population.length; i++) {
    population[i] = new DNA();
  }
}
 
void draw() {
frameRate(20);
background(0);
fill(247,217,107);
rect(10,10,780,280);
  for (int i = 0; i < population.length; i++) {
    population[i].fitness();
  }
 

  ArrayList<DNA> matingPool = new ArrayList<DNA>();
 
  for (int i = 0; i < population.length; i++) {
    int n = int(population[i].fitness * 100);
    for (int j = 0; j < n; j++) {
      matingPool.add(population[i]);
    }
  }
 
  for (int i = 0; i < population.length; i++) {
    int a = int(random(matingPool.size()));
    int b = int(random(matingPool.size()));
    DNA partnerA = matingPool.get(a);
    DNA partnerB = matingPool.get(b);
    DNA child = partnerA.crossover(partnerB);

    child.mutate(mutationRate);
 
    population[i] = child;
  textFont(font1);
    population[i].display(i);
   
    
  }
  saveFrame("frame-####.png");
}

class DNA {
 
 
  char[] genes;
  float fitness;
  int b;
 

  DNA() {
    genes = new char[target.length()];
    for (int i = 0; i < genes.length; i++) {
      genes[i] = (char) random(32,128);
    }
  }
 

  void fitness() {
     int score = 0;
     for (int i = 0; i < genes.length; i++) {
        if (genes[i] == target.charAt(i)) {
          score++;
        }
     }
     fitness = float(score)/target.length();
  }
 

  DNA crossover(DNA partner) {
    DNA child = new DNA();
    int midpoint = int(random(genes.length));
    for (int i = 0; i < genes.length; i++) {
      if (i > midpoint) child.genes[i] = genes[i];
      else              child.genes[i] = partner.genes[i];
    }
    return child;
  }
 

  void mutate(float mutationRate) {
    for (int i = 0; i < genes.length; i++) {
      if (random(1) < mutationRate) {
        genes[i] = (char) random(32,128);
      }
    }
  }
 
void display(int a){
  b=a;
   fill(247,217,107);
rect(10,10,880,280);
  for (int i = 0; i < genes.length; i++) {
    float w=random(15,width-15);
    float h=random(15,height-15);
    
    
      fill(random(255),random(255),random(255));
   textSize(40);
  
    text(genes[i],62+40*i,160);
    if(i%3==0){
      noStroke();
    ellipse(w,h,12,12);
    }
    
  }

  
  
  
}
}
