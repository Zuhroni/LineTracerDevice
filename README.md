
#include <ArduinoRobot.h>
#include <Wire.h>
#include <SPI.h>

#define VALUE  300
#define VALUESTOP 987

void setup() {
  Robot.begin();
  Robot.stop();
}

void loop() {

  if ( (Robot.Front_IRread(2) < VALUE) || (Robot.Front_IRread(3) < VALUE) )
    Robot.motors(-125, -125);

  if ( (Robot.Front_IRread(0) < VALUE) || (Robot.Front_IRread(1) < VALUE) )
    Robot.motors(-125, 0);

  if ( (Robot.Front_IRread(4) < VALUE) || (Robot.Front_IRread(5) < VALUE) )
    Robot.motors(0, -125);

  if ( (Robot.Front_IRread(0) < VALUE) && (Robot.Front_IRread(1) < VALUE) && (Robot.Front_IRread(2) < VALUE) && (Robot.Front_IRread(3) < VALUE) && (Robot.Front_IRread(4) < VALUE) && (Robot.Front_IRread(5) < VALUE) )
    Robot.motors(-125, -100);

  if ( (Robot.Front_IRread(3) < VALUE) && (Robot.Front_IRread(4) < VALUE) && (Robot.Front_IRread(5) < VALUE) )
    Robot.motors(0, -100);
  
  if( (Robot.Front_IRread(0) > VALUESTOP) || (Robot.Front_IRread(1) > VALUESTOP) || (Robot.Front_IRread(2) > VALUESTOP) || (Robot.Front_IRread(3) > VALUESTOP) || (Robot.Front_IRread(4) > VALUESTOP) || (Robot.Front_IRread(5) > VALUESTOP) )
        Robot.motors(0, 0);
  
  delay(35);
}

