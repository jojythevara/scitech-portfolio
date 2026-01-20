# Friday:
**[Go back](/posts/blog.md)**
a. I used these buffs for explosion, I implemented them by making it so the player would become very big for one second before turning back to normal.

b. I used the variables in the powerUp function to check for collision with an explosion power up and then use the variables to apply the explosion, specifically by setting p1Size to explosionSize for one second, and set booleans for whether the power up was exploding or not.

c. Something I found hard was figuring the perfect time to make the slime giant to make it look smooth, I chose one millisecond. 

int buffDuration = 6000; // 6 seconds

// Player 1 buffs

boolean p1SizeBuff = false;

boolean p1SpeedBuff = false;

int p1BuffStart;

int p1BaseSize = 100;

int p1BaseSpeed = 5;

// Player 2 buffs

boolean p2SizeBuff = false;

boolean p2SpeedBuff = false;

int p2BuffStart;

int p2BaseSize = 100;

int p2BaseSpeed = 5;

// Explosion settings

int explosionSize = 600;      // how big the player gets

int explosionDuration = 1; // 1 millisecond

// Player 1 explosion state

boolean p1Exploding = false;

int p1ExplosionStart = 0;

// Player 2 explosion state

boolean p2Exploding = false;

int p2ExplosionStart = 0;
