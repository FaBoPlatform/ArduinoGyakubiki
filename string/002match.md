# 文字列を条件判定

## 文字列のマッチ

```c
void setup() {
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }
}

void loop() {
  if(Serial.available() > 0) {
  
    // 改行コード(10)を検出したら、そこまでの文字列を取得
    String input = Serial.readStringUntil(10);
    Serial.flush();
    // 改行コードを取り除く
    input.trim();

    if(strcmp(input, "TEST WORD") == 0) {
      Serial.println("MACTH");
    } else {
      Serial.println("UNMACTH");
    }
  }
}

```

