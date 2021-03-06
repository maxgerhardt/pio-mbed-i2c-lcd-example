﻿# PlatformIO I²C-LCD Example with mbed-os

## Notes

A compilation error in the TaskManagerIO library is expected. See https://github.com/davetcc/TaskManagerIO/issues/17 for fix.

## Description

Uses the library https://github.com/davetcc/LiquidCrystalIO to implement talking to an LCD screen which is connected to an I2C port expander via PCF8574 (although other types like MCP23017 are also supported by the underlying library).

It only compiles for the Nucleo L476RG now and not for the other STM32F051R8 because of size limitations, but it's still there for reference. 

## Pinout

Your board's default I2C pins have to be connected to the I2C LCD module. Make sure to check whether the I2C pins in the firmware are correct.

Then, take care that the pinmapping between the I2C GPIO expander and the LCD screen is as expected. The firmware currently uses the popular mapping 

```cpp
const int rs = 0, en = 2, d4 = 4, d5 = 5, d6 = 6, d7 = 7;
..
lcd.configureBacklightPin(3);
```

mapping between P7..P0 pins of the I2C expander and the LCD. 

A reference module can be seen at https://handsontec.com/dataspecs/module/I2C_LCD_Interface.pdf. 
