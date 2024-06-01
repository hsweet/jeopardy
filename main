/* #include <LiquidCrystal_I2C.h>

#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4
LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);
*/

const int resetTime = 1000;
const int enableLED = 8;
bool ready = 0;
int presses[20];  // game history
int cnt = 0;

// inputs pin 4,5,6,7
// outputs 10,11,12,13
// inputs pins go LOW when pressed

void setup() {
  pinMode(enableLED, OUTPUT);
  digitalWrite(enableLED, HIGH);
/*
  // LCD setup
  lcd.init();
  lcd.backlight();
  lcd.setCursor(5, 0);
  lcd.print("Jeopardy!");
  lcd.setCursor(1, 2);
  lcd.print("Get Ready to Play!");
*/
  // switches
  for (int i = 4; i < 8; i++) {
    pinMode (i, INPUT);
    digitalWrite(i, INPUT_PULLUP);  // enable pullups
  }
  // leds
  for (int j = 10; j < 14; j++)
    pinMode(j, OUTPUT);

  // check for stuck button
}

void loop() {

  for (int i = 4; i < 8; i++) {
    if (digitalRead(i) == LOW) {
      // record press
      presses[cnt] = i;
      cnt++;

      /*
      lcd.clear();
      lcd.setCursor(4, 0);
      lcd.print("Button #");
      lcd.setCursor(13, 0);
      lcd.print(i - 3); // Buttons 1-4 connect to pins 4-7
      */
      digitalWrite(enableLED, LOW);
      marquee(i);
      reset(i);
    }
  }
}

void marquee(int firstPin) {

  tone(9, 262, 250); // Plays 262Hz tone for 0.250 seconds

  for (int i = 0; i < 4; i++) {
    for (int j = 10; j < 14; j++) {
      digitalWrite(j, HIGH);
      delay (100);
      digitalWrite(j, LOW);
    }
  }


  digitalWrite(firstPin + 6, HIGH);
  delay(resetTime);

  for (int i = 10; i < 14; i++) {
    digitalWrite(i, HIGH);
  }

  delay(1000);
  for (int i = 10; i < 14; i++) {
    digitalWrite(i, LOW);
  }
/*
  lcd.setCursor(2, 0);
  lcd.print("Next Question...");
*/
}

void reset(int heldPin) {
  // don't restart until all the buttons are reset
  while (digitalRead(heldPin) == LOW) {
    /*
    lcd.clear();
    lcd.setCursor(3, 0);
    lcd.print("Unlock button");
    */
    delay(1000);
    // lcd.clear();
    delay(1000);

  }
  //}

}
