# Monday:
**[Go back](/posts/blog.md)**

a. I used selection today to control the prompts for starting the game. I used an if statement to check whether the variable “gameOn” was true. gameOn would only become true if the user clicked ENTER, specifically on the start screen. I also used selection to check if the player had finished selecting their character by clicking SPACE. 

b. I implemented it this way because if I didn't the player wouldn’t be able to access the character selection or the actual game. 

c. Some challenges I encountered during coding was the fact that if the player clicked ENTER during the gameplay, it would flash back to the start screen. I fixed this by making sure that gameOn would become false when ENTER was pressed while gameOn was already true.


//other

PImage startScreen, screen, winP1, winP2, selectColor, p1Slime, p2Slime, redSlime, blueSlime, greenSlime, purpleSlime;

PFont pixel;

 

//int

int canvasWidth = 800;

int canvasHeight = 800;

int scoreP1 = 0;

int scoreP2 = 0;

int[] canvas = new int[canvasWidth * canvasHeight];


  //images

  imageMode(CENTER);

  startScreen = loadImage("startScreen.png");

  winP1 = loadImage("winP1.png");

  winP2 = loadImage("winP2.png");

  selectColor = loadImage("selectColor.png");

  screen = startScreen;


void draw() {

  image(screen, width/2, height/2, width, height); //start screen

  if (gameOn) {

    //set game background

    screen = startScreen;

}
