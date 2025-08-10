![Alternative Text](https://raw.githubusercontent.com/leonardoalvessousa/AVR_WDT/refs/heads/main/AVR_BANNER.jpg)

## Introduction

This article explores the **`Device Watchdog Timer (WDT)`** circuit, present in Microchip Technology’s AVR® devices. The **`WDT`** is a crucial safety mechanism that ensures system stability. It is useful for detecting software or hardware failures, preventing the system from getting stuck in an error state.

### Simplified Diagram

The `WDT` works as a counter that increments with each clock cycle of an independent on-chip oscillator (O\_WDT). When the counter reaches a predefined value, called the timeout, the `WDT` triggers and forces a system reset.

![Alternative Text](https://raw.githubusercontent.com/leonardoalvessousa/AVR_WDT/refs/heads/main/BlocDiagram.jpg)

### Enabling the WDT

Practical example using the ATmega328p chip in the Arduino IDE:

```IDE_Arduino
// C++

#include <avr/wdt.h>

void setup() 
{
  wdt_enable(WDTO_2S);
}
void loop() 
{
  // Main task
}
```

> **Including the WDT library**

* **#include:** This directive tells the compiler to include the `avr/wdt.h` header file.
* **avr/wdt.h:** This header file contains the definitions and functions needed to work with the WDT on AVR devices.

> **Initial task**

* **void setup():** This function is called once at the beginning of the program. It’s where you set up your program’s initial configuration.
* **wdt\_enable():** This function, defined in `avr/wdt.h`, enables the WDT.
* **WDTO\_2S:** This constant, also defined in `avr/wdt.h`, sets the WDT timeout to 2 seconds.

> \[!NOTE]
> There are other predefined TIME values available in the `avr/wdt.h` library:
>
> `wdt_enable(WDTO_8S);`
> `wdt_enable(WDTO_4S);`
> `wdt_enable(WDTO_1S);`
> `wdt_enable(WDTO_500MS);`
> `wdt_enable(WDTO_250MS);`
> `wdt_enable(WDTO_1200MS);`
> `wdt_enable(WDTO_60MS);`
> `wdt_enable(WDTO_30MS);`
> `wdt_enable(WDTO_15MS);`
>
> Second (S), Millisecond (MS)

> **Main task/loop**

* **void loop():** This function is called repeatedly after `setup()` has been executed.

### Final considerations

Always check for common delays in the main task, such as `delay()` calls or subfunctions with multiple complex tasks. These delays must be considered when choosing the timer value for `wdt_enable()`.

> \[!CAUTION]
> Avoid unnecessary resets caused by the algorithm’s normal processes. Do some calculations first!

## 😼 Author

🐈‍⬛ @leonardoalvessousa

## 🎁 How to show appreciation

* Tell others about this project 📢
* Buy the author a beer **[🍺](https://nubank.com.br/cobrar/f7g6w/6755dd2c-8e3d-4c14-9976-b1afefc8ae07)**

---
