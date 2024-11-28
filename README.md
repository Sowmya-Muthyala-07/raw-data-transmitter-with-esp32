#include <IRremote.h>

#define IR_SEND_PIN 32 // Pin where the IR LED is connected

// Use uint16_t instead of unsigned int for raw data
uint16_t turnOnRawData[] = {
  3300, 1600, 450, 400, 450, 350, 450, 1200, 400, 450, 
  400, 1200, 400, 450, 400, 400, 400, 400, 400, 1250, 
  400, 1250, 400, 400, 400, 400, 400, 450, 400, 1200,
  400, 1250, 400, 400, 450, 400, 400, 400, 400, 400,
  400, 450, 400, 400, 400, 400, 400, 450, 400, 400,
  400, 400, 400, 400, 450, 400, 400, 400, 400, 400,
  1250, 400, 400, 450, 400, 400, 400, 400, 400, 450,
  400, 400, 400, 400, 400, 450, 1200, 400, 450, 400,
  400, 400, 400, 400, 400, 450, 1200, 400, 1250, 400,
  1200, 450, 1200, 400, 1250, 400, 1200, 450, 1200, 
  400, 1250, 400, 400, 450, 400, 400, 1200, 450, 400, 
  400, 400, 400, 400, 450, 400, 400, 400, 400, 400, 
  450, 400, 400, 400, 400, 1250, 400, 1200, 450, 400, 
  400, 400, 400, 1250, 400, 400, 400, 450, 400, 400, 
  400, 400, 400, 1250, 400, 400, 450, 1200, 400, 1250, 
  400, 400, 400, 450, 400, 400, 400, 400, 400, 450, 
  400, 400, 400, 400, 400, 1250, 400, 1250, 400, 400, 
  400, 400, 400, 450, 400, 400, 400, 400, 400, 450, 
  400, 400, 400, 400, 400, 450, 400, 400, 400, 400, 
  400, 450, 400, 400, 400, 400, 400, 450, 400, 400, 
  400, 400, 400, 450, 400, 400, 400, 400, 400, 450, 
  400, 400, 400, 400, 400, 450, 400, 400, 400, 400, 
  400, 450, 400, 400, 400, 400, 400, 450, 400, 400, 
  400, 400, 400, 1250, 400, 400, 400, 450, 400, 1200, 
  400, 1250, 400, 400, 400, 1250, 400, 400, 400, 450, 
  400, 400, 400, 500, 400
};

void sendIRSignal(uint16_t *rawData, size_t length) {
  IrSender.sendRaw(rawData, length, 38); // 38kHz frequency
  Serial.println("IR signal sent!");
}

void setup() {
  Serial.begin(4800);
  IrSender.begin(IR_SEND_PIN); // Initialize IR sender
  Serial.println("IR Sender ready");
}

void loop() {
  sendIRSignal(turnOnRawData, sizeof(turnOnRawData) / sizeof(turnOnRawData[0]));
  delay(5000); // Delay between sending signals
}
