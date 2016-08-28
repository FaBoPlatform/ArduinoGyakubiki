# Serial通信のバッファサイズを変更する

## Arduinoのスペック

|型番|MCU|Clock|Flash|SRAM|EEPROM|
|:--|:--|
|UNO|ATmega328P|16 MHz|32 KB|2 KB|1 KB|
|MEGA256|ATmega2560|16 MHz|256 KB |8 KB|5 KB|
|101|Intel Curie|32 MHz|196 kB|24 KB| |
|ZERO|ATSAMD21G18|48 MHz|256 KB|32 KB| |
|DUE|AT91SAM3X8E|84 MHz|512 KB|96 KB| |

## ArduinoのSerial通信のBufferサイズ

|型番|Serial通信のBufferサイズ|
|:--|:--|
|UNO,MEGA256|16 Byteもしくは64 Byte|
|DUE|128 Byte|

### UNO, MEGA系のSerial通信のBufferサイズの変更

Arduino UNOとMEGA系は、下記フォルダのHardwareSerial.hの`SERIAL_RX_BUFFER_SIZE`と`SERIAL_TX_BUFFER_SIZE`でSerial通信のBufferサイズを定義している。

> /Applications/Arduino.app/Contents/Java/hardware/arduino/avr/cores/arduino
> /Applications/Arduino.app/Contents/Java/hardware/arduino/avr/cores/arduino_256

`Serial`、`Serial1`、`Serial2`、`Serial3`に対応して、下記ヘッダーでサイズが定義されている。

* [HardwareSerial.h](https://github.com/arduino/Arduino/blob/master/hardware/arduino/avr/cores/arduino/HardwareSerial.h)
* [HardwareSerial1.h](https://github.com/arduino/Arduino/blob/master/hardware/arduino/avr/cores/arduino/HardwareSerial1.h)
* [HardwareSerial2.h](https://github.com/arduino/Arduino/blob/master/hardware/arduino/avr/cores/arduino/HardwareSerial2.h)
* [HardwareSerial3.h](https://github.com/arduino/Arduino/blob/master/hardware/arduino/avr/cores/arduino/HardwareSerial3.h)


```bash
#if !defined(SERIAL_TX_BUFFER_SIZE)
#if ((RAMEND - RAMSTART) < 1023)
#define SERIAL_TX_BUFFER_SIZE 16
#else
#define SERIAL_TX_BUFFER_SIZE 64
#endif
#endif
#if !defined(SERIAL_RX_BUFFER_SIZE)
#if ((RAMEND - RAMSTART) < 1023)
#define SERIAL_RX_BUFFER_SIZE 16
#else
#define SERIAL_RX_BUFFER_SIZE 64
#endif
```

ここがSerialBufferの上限になるので、増やしたい場合は、必要なサイズに書き直す。

### DUE系のSerial通信のBufferサイズの変更

DUE系のコアは、BoardManager経由でインストールされるため、ローカルでは下記フォルダに展開される。

> ~/Library/Arduino15/packages/arduino/hardware/sam/1.6.9/cores/arduino/

SERIAL_BUFFER_SIZEは、[RingBuffer.h](https://github.com/arduino/Arduino/blob/master/hardware/arduino/sam/cores/arduino/RingBuffer.h)で定義されている。

```bash
#define SERIAL_BUFFER_SIZE 128
```

ここがSerialBufferの上限になるので、増やしたい場合は、必要なサイズに書き直す。

## 確認(共通)

変更後は、Arduinoのスケッチで、SERIAL_BUFFER_SIZEをプリントし、変更した値と同じなら反映される。

```c
Serial.println(SERIAL_BUFFER_SIZE);
```

