# 文字列を表示する

## ASCII文字

|char|byte|int||char|byte|int||char|byte|int||char|byte|int|
|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|:--|
|0|0x30|48| |;|0x3B|59| |F|0x46|70| |Q|0x51|81|
|1|0x31|49| |<|0x3C|60| |G|0x47|71| |R|0x52|82|
|2|0x32|50| |=|0x3D|61| |H|0x48|72| |S|0x53|83|
|3|0x33|51| |>|0x3E|62| |I|0x49|73| |T|0x54|84|
|4|0x34|52| |?|0x3F|63| |J|0x4a|74| |U|0x55|85|
|5|0x35|53| |@|0x40|64| |K|0x4b|75| |V|0x56|86|
|6|0x36|54| |A|0x41|65| |L|0x4c|76| |X|0x57|87|
|7|0x37|55| |B|0x42|66| |M|0x4d|77| |Y|0x58|88|
|8|0x38|56| |C|0x43|67| |N|0x4e|78| |W|0x59|89|
|9|0x39|57| |D|0x44|68| |O|0x4f|79| |Z|0x5a|90|
|:|0x3A|58| |E|0x45|69| |P|0x50|80|

## ASCII文字を出力する

```c
void setup() { 
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }

  for(int i = 48; i < 127; i++){
    Serial.write(i);
    Serial.print("  ");
    Serial.print(i,HEX);
    Serial.print("  ");
    Serial.print(i);
    Serial.println();
  }
}

void loop() {
}
```


## String型の文字を表示

```c
void setup() { 
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }

  // String型の文字列を表示
  Serial.println("String TEST");
}

void loop() {
}
```
結果 
> String TEST

## String型に文字を代入して表示

```c
void setup() { 
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }

  // CHAR型の文字列を表示
  string word = "String TEST";
  Serial.println(word);
}

void loop() {
}
```
結果
>  String TEST


## CHAR型のポインタに文字を代入して表示

```c
void setup() { 
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }

  // CHAR型の文字列を表示
  chat *word = "String TEST";
  Serial.println(word);
}

void loop() {
}
```
結果
>  String TEST


## 各種形式での出力

```c
void setup() { 
  Serial.begin(115200);
  while (!Serial) {
    ; 
  }

  int value = 31;
  Serial.println(value, BIN); // ビット
  Serial.println(value, OCT); // 8進数
  Serial.println(value, DEC); // 10進数
  Serial.println(value, HEX); // 16進数
}

void loop() {
}
```
結果
> 11111<br>
37<br>
31<br>
1F<br>


