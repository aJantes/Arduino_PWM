# Arduino_PWM

## 功能
通过控制 bpibit 上的PWM ，使之出现呼吸灯的效果

## 代码
```c++

#include <Arduino.h>

int freq = 2000;  // 频率
int channel = 0;  // 通道
int resolution = 8; // 分辨率

void setup()
{
  ledcSetup(channel, freq, resolution);
  ledcAttachPin(18, channel); // 将通道连接到对应的引脚上
}

void loop()
{
  for (int dutyCycle = 0; dutyCycle <= 250; dutyCycle = dutyCycle + 5)
  {
    ledcWrite(channel, dutyCycle);
    delay(20);
  }

  for (int dutyCycle = 250; dutyCycle >= 0; dutyCycle = dutyCycle - 5)
  {
    ledcWrite(channel, dutyCycle);
    delay(20);
  }
}
```