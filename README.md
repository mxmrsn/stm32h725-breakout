# STM32H725-Breakout

![STM Bootloader & DFU](/resources/project.png)
![chip configuration](/resources/chip-configuration.png)

## Flash Layout
The memory of the chip is configured where the first 128kB are dedicated to the bootloader, then the rest is for the main application. Seee in ```../bootloader/Core/Src/main.c```:

```
#define APP_ADDRESS 0x08020000
```

## Clock Configuration
The clock is optimized to run 48MHz on the USB comms, and ~530Hz main clock rate.

## DFU Trigger
To put the chip into bootloader mode, we configure this by holding GPIO PC10 button down. Then the LED connected to GPIO PC11 should heartbeat at 1Hz. 