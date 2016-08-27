# ArduinoUnitでUnitテストする

## ライブラリをインストール

![](/img/library/001_1.png)

![](/img/library/001_2.png)

![](/img/test/001_1.png)

## サンプル

```c
#line 2 "basic.ino"
#include <ArduinoUnit.h>

test(correct)
{
  int x=1;
  assertEqual(x,1);
}

test(incorrect)
{
  int x=1;
  assertNotEqual(x,1);
}

void setup()
{
  Serial.begin(9600);
  while(!Serial); // for the Arduino Leonardo/Micro only
}

void loop()
{
  Test::run();
}
```