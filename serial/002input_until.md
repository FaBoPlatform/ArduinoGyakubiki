# Serial Concoleから文字列を取得

```c
#include "Arduino.h"

void setup() { 
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }
  Serial.println("Init");
}

void loop() {
  if(Serial.available() > 0) {
  	// 改行コード(10)を検出したら、そこまでの文字列を取得
    String input = Serial.readStringUntil(10);
    Serial.flush();
    // 改行コードを取り除く
    input.trim();
    
    if(input == "TEST"){
     	Serial.println("Got test");
    } else if(input == "1") {
    	Serial.println("Got 1");
    }
  }
}
```