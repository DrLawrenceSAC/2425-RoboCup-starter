# 2425-RoboCup-starter

Use the code below to set up all sensors/motors using the SACBOT-V6


```C++
const int leftLine = A0;
const int midLine = A1;
const int rightLine = A2;

// Setting up variables for motor pins (system on/off, speed and direction)
const int motorsOn = 3;
const int leftSpeed = 5;
const int rightSpeed = 6;
const int leftDir = 7;
const int rightDir = 8;

// setting up ultrasonic
const int trig = 13;
const int echo = 12;



void setup() {
  // setting up the serial monitor and sensor pins
  Serial.begin(9600);
  pinMode(leftLine, INPUT);
  pinMode(midLine, INPUT);
  pinMode(rightLine, INPUT);

  // setting up ultrasonic sensors as input/output
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);


  // setting up motor pins as output
  pinMode(motorsOn, OUTPUT);
  pinMode(leftSpeed, OUTPUT);
  pinMode(rightSpeed, OUTPUT);
  pinMode(rightDir, OUTPUT);
  pinMode(leftDir, OUTPUT);
  // turn on all the motors
  digitalWrite(motorsOn, HIGH);
  // set the speed of left and right to 30 (max is 255)
  analogWrite(leftSpeed, 30);
  analogWrite(rightSpeed, 30);
  // turn motors on running forward
  digitalWrite(leftDir, HIGH);
  digitalWrite(rightDir, HIGH);
  // wait half a second
  delay(500);
  // turn off motors (speed 0)
  analogWrite(leftSpeed, 0);
  analogWrite(rightSpeed, 0);
}

void loop() {
  // reading ultrasonic sensor:
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(20);
  digitalWrite(trig, LOW);
  float duration = pulseIn(echo, HIGH);
  float distance = duration / 58;
  // printing out distance values
  Serial.print("distance: ");
  Serial.print(distance);

  // reading the sensors and saving their values in _Dark variables
  int leftDark = analogRead(leftLine);
  int midDark = analogRead(midLine);
  int rightDark = analogRead(rightLine);
  // printing out results to the serial monitor.
  Serial.print("  Dark readings - Left: ");
  Serial.print(leftDark);
  Serial.print(" Middle: ");
  Serial.print(midDark);
  Serial.print(" Right: ");
  Serial.println(rightDark);

  /// add code here for motor control and use of sensors
  // Goal 1 - wall avoidance - use the ultrasonic sensor to avoid walls
  // Goal 2 - spot sensing - get the robot to stop on a white or black spot
  // Goal 3 - line following - get the robot to turn towards a black line
  

}
```
