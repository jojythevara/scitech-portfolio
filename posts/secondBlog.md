# Tuesday:

a. Today, I used variable and data tracking for the use of gameOn, characterChosen, and score. I used the variables to properly display the GUI in the game. 

b. I used gameOn and characterChosen in a method I made called keyPressed, this method is used to check when enter and space was presesd to move from the start screen to the character select. I also used a scoreP1 and a scoreP2 variable when displaying the score.

c. The challenge I faced was finding a good font for the score. I had to check the Processing forums to see a list of supported fonts and found that OCR A Extended was the optimal choice.

Code:

//score
      fill(241, 213, 119);
      textAlign(CENTER);
      textSize(40);
      text(("" + scoreP1 + "-" + scoreP2), width/2, height - 755);

void keyPressed () {

  //check if the enter key is pressed to start character selection

  if (keyCode == ENTER & gameOn == false) {

    gameOn = true;

  }

  //check if the space key is pressed to start the game

  if (keyCode == ' ' && characterChosen == false && P1 != 0 && P2 != 0) {

    characterChosen = true;

  }


