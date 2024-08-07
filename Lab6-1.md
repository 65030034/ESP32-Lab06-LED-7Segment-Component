# Lab 6-1 ทดสอบ  Hardware 7 segment

## 1. ต่อวงจรดังนี้

| Segment | ESP32 Pin |
|:-------:|:---------:|
|     a   | 16        |
|     b   | 17        |
|     c   | 5         |
|     d   | 18        |
|     e   | 19        |
|     f   | 21        |
|     g   | 22        |
| digit 1 | 0         |
| digit 2 | 4         |




## 2. สร้าง project และเขียนโปรแกรม 

2.1  สร้าง esp project

2.2 add idf_component.yml ใน Main component
  
   2.1 เพิ่ม dependency ใน yml

```yml
dependencies:
  LED:
    git: https://github.com/koson/LED_Test.git 
    path: components/LED
```

2.3 เปลี่ยนชื่อ main.c เป็น main.cpp

2.4 ใน CMakeLists.txt เปลี่ยนชื่อ main.c เป็น main.cpp

2.5 ใน main.cpp เปลี่ยน code เป็นดังนี้

```cpp
#include <stdio.h>
#include "LED.h"
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"

LED seg_a(16);
LED seg_b(17);
LED seg_c(5);
LED seg_d(18);
LED seg_e(19);
LED seg_f(21);
LED seg_g(22);
LED digit_1(0);
LED digit_2(4);

extern "C" void app_main(void)
{

    while(1)
    {
    digit_1.ON();
    digit_2.OFF();    
    seg_a.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_b.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_c.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_d.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_e.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_f.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_g.ON();
    vTaskDelay(500/portTICK_PERIOD_MS);
 
 

    vTaskDelay(500/portTICK_PERIOD_MS);
    digit_1.OFF(); 
    digit_2.ON(); 
    vTaskDelay(500/portTICK_PERIOD_MS);

    seg_a.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_b.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_c.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_d.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_e.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_f.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);
    seg_g.OFF();
    vTaskDelay(500/portTICK_PERIOD_MS);


    } 

}
```

2.6 build และทดสอบโปรแกรม