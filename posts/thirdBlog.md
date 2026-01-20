# Wednesday:
**[Go back](/posts/blog.md)**

a. Today, I did the timer. I used variable and tracking data to create a variety of variables for the timer, and time-related variables. 

b. I used it before setup, in a separate class. I created a variable called countdownTime for the constantly ticking timer. Additionally, I also created variable called s, which was meant to store the countdownTime in a string. The variable timer was used so that countdownTime would go down every 1000 milliseconds or one second. 

c. I struggled trying to figure out what millis() did, so I did experiment using currentTime and increasing it every second. I eventually realized that millis() meant total time since the application was run, not just when I clicked the enter key.

Code:

class Timer {

  //props

  int startTime;

  int interval;

  

  //constructor

   Timer(int timeInterval) {

     interval = timeInterval; 

   }

   

   //methods

   void start() {

     startTime = millis(); 

   }

   

   boolean complete() {

     int elapsedTime = millis() - startTime;

     if (elapsedTime > interval) {

       return true; 

     }

     else {

       return false; 

     } //end if

   }//end complete

}//end class

Timer timer;

int currentTime;

int countdownTime;

String s

; 

void setup() {

  timer = new Timer(1000);

  s = "";

  currentTime = 0;

  countdownTime = 60;

}

      //timer stuff

      if (timer.complete() == true) {

        if (countdownTime > 0) {

          countdownTime--;

          timer.start();

        }

        else {

           gameOn = false;

        }

      }

      //text stuff

      

      fill(255);

      textSize(150);

      textAlign(CENTER);

      s = "" + countdownTime;

      text(s, width/2, height/2+50);
