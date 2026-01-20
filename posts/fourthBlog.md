# Thursday:
**[Go back](/posts/blog.md)**

a. Today, I used a selection structure for the application of different power ups within our game. 

b. This involved spawning three random powerups, every 10 seconds, resetting the effect every 6, adding the individual effects, and applying them seperately to the players. The different power ups were size, speed, and explosion. Size increases the player's size, speed increases the player's speed, and explosion creates a large area of painted space.

c. The most diffucult part was making sure the power-ups applied seperately to each player. I solved this by adding a parameter in apply powers, that asked which player had collided with the object. 

void powerUp () {
  if (millis() - lastSpawnTime >= spawnInterval) {
    if (!powerExists) {
      spawnPowerUp();
    }
    lastSpawnTime = millis();
  }

  // draw power-up if it exists
  if (powerExists) {
    drawPowerUp();


    if (isCollided(powerX, powerY, 100, 100, p1X, p1Y, p1Size, p1Size)) {
      applyPowerUp(1);
      powerExists = false;
    }
    if (isCollided(powerX, powerY, 100, 100, p2X, p2Y, p2Size, p2Size)) {
      applyPowerUp(2);
      powerExists = false;
    }
  }

  //check for size & speed buffs
  // Player 1 size buff timer
  if (p1SizeBuff && millis() - p1BuffStart >= buffDuration) {
    p1Size = p1BaseSize;
    p1SizeBuff = false;
  }

  // Player 1 speed buff timer
  if (p1SpeedBuff && millis() - p1BuffStart >= buffDuration) {
    p1Speed = p1BaseSpeed;
    p1SpeedBuff = false;
  }

  // Player 2 size buff timer
  if (p2SizeBuff && millis() - p2BuffStart >= buffDuration) {
    p2Size = p2BaseSize;
    p2SizeBuff = false;
  }

  // Player 2 speed buff timer
  if (p2SpeedBuff && millis() - p2BuffStart >= buffDuration) {
    p2Speed = p2BaseSpeed;
    p2SpeedBuff = false;
  }
  
  //check for explosion buffs
  // Player 1 explosion timer
  if (p1Exploding && millis() - p1ExplosionStart >= explosionDuration) {
    p1Size = p1BaseSize;
    p1Exploding = false;
  }
  
  // Player 2 explosion timer
  if (p2Exploding && millis() - p2ExplosionStart >= explosionDuration) {
    p2Size = p2BaseSize;
    p2Exploding = false;
  }
}

void spawnPowerUp() {
  powerX = int(random(50, 750));
  powerY = int(random(150, 750));
  //powerType = int(random(3));
  powerType = 2;
  powerExists = true;
}

void applyPowerUp(int player) {
  if (powerType == 0) {
    if (player == 1) {
      p1BaseSize = p1Size;
      p1Size += 100;
      p1SizeBuff = true;
      p1BuffStart = millis();
    } else {
      p2BaseSize = p2Size;
      p2Size += 100;
      p2SizeBuff = true;
      p2BuffStart = millis();
    }
  }
  else if (powerType == 1) {
    if (player == 1) {
      p1BaseSpeed = p1Speed;
      p1Speed += 6;
      p1SpeedBuff = true;
      p1BuffStart = millis();
    } else {
      p2BaseSpeed = p2Speed;
      p2Speed += 6;
      p2SpeedBuff = true;
      p2BuffStart = millis();
    }
  }
  
  else if (powerType == 2) {
    if (player == 1) {
      p1BaseSize = p1Size;
      p1Size = explosionSize;
      p1Exploding = true;
      p1ExplosionStart = millis();
    }
    else {
      p2BaseSize = p1Size;
      p2Size = explosionSize;
      p2Exploding = true;
      p2ExplosionStart = millis();
    }
  }
}

void drawPowerUp () {
  if (powerType == 0) {
    image(giant, powerX, powerY, powerSize, powerSize);
  } else if (powerType == 1) {
    image(speed, powerX, powerY, powerSize, powerSize);
  } else if (powerType == 2) {
    image(explosion, powerX, powerY, powerSize, powerSize);
  }
}

boolean isCollided (int x1, int y1, int w1, int h1, int x2, int y2, int w2, int h2) {
  return x1 < x2 + w2 &&
    x1 + w1 > x2 &&
    y1 < y2 + h2 &&
    y1 + h1 > y2;
}
