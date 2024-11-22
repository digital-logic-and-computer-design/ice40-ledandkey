# LED & Key iCE 40

iCE40 Verilog driver for the LED & Key modules/boards (HW-154) based on the [TM1638](https://www.makerhero.com/img/files/download/TM1638-Datasheet.pdf).

## Parameters

* `CLICK_DIV_X2`:  Default is 16, which is suitable for a 6MHz clock.  ClockPeriod/CLICK_DIV_X2 should exceed 1uS for the delay required to read keys.

## Ports

* `clock`: Main clock
* `reset`: Reset. Needs to be reset to initialize LED & Key module.
* `display0`: Right-most 7-segment display / one's digit
* `display1`: ten's digit
* `display2`: hundreds digit
* `display3`: thousands digit
* `display4`: ten thousands digit
* `display5`: hundred thousands digit
* `display6`: millions digit
* `display7`: ten millions digit
* `leds`: LEDs along the top
* `keys`: The last red values of the keys
* `tm_strobe`: Pin connected to the LED & Key's strobe (`STB`) pin
* `tm_clock`: Pin connected to the LED & Key's clock (`CLK`) pin
* `tm_dio`: Pin connected to the LED & Key's digital I/O (`DIO`) pin

### Display Layout / Mapping

Each `display` represents a full 7-segment display and decimal with a conventional layout.

```
 +-a-+
 |   |
 f   b
 |   |
 +-g-+
 |   |
 e   c
 |   |
 +-d-+ h

8-bit value: hgfe dcba 
```

`display0 = 0'b0000_0110` would be a 1 (segments b and c);

### LEDs Layout / Mapping

The most significant bit (`leds[7]`) is the left-most LED (LED1), the least significant bit (`leds[0]`) is the right-most LED (LED8), etc.

### Keys Layout / Mapping

The most significant bit (`keys[7]`) is the left-most switch (SW1), the least significant bit (`keys[0]`) is the right-most switch (SW8), etc.

# TODO

Rename the ports to align with the silkscreen names on the LED & Key module.

# Author 

Bill Siever <bsiever@gmail.com>