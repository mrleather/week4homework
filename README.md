# week4homework
PImage img;
int numFrames=8;
int frame=0;
PImage[] images=new PImage[numFrames];
void setup() {
  size(500, 500);
  for (int i =0; i<=7; i++) {
    images[i]=loadImage(i+".png");
  }
}

void draw() {
  //image(img,0,0);
  loadPixels ();
  for (int i=0; i<=7; i++) {
    images[i].loadPixels();
    for (int y=0; y<images[i].height; y++) {
      for (int x=i; x<images[i].width; x+=7) {
        //if(x>200){
        //x=0;}
        int loc=x+y*images[i].width;
        float r=red(images[i].pixels[loc]);
        float g=green(images[i].pixels[loc]);
        float b=blue(images[i].pixels[loc]);
        pixels[loc]=color(r, g, b);
      }
    }
  }

  updatePixels();
  save("DEER.jpg");
}
