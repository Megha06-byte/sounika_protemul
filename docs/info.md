## How it works

A programmable protocol emulator. A small 2-stage, 2-thread barrel processor runs
protocol programs (UART, SPI, I2C, and more) with cycle-exact timing. Every instruction
takes 1 + delay ticks, so pin edges are fully predictable. Each thread has its own
program counter, scratch registers (X, Y), shift registers (ISR/OSR), clock divider
and pin mapping. The host loads programs and configuration over an SPI interface,
so new protocols can be added after fabrication without hardware changes.

Work in progress: the design currently contains the template example and is being
replaced step by step.

## How to test

1. Use the RP2040 on the demo board as the host, connected to the host SPI pins.
2. Write a protocol program (for example UART TX) into instruction memory over SPI.
3. Configure the thread (clock divider, pins) and enable it.
4. Send bytes to the TX FIFO and observe the UART TX pin with a logic analyzer
   or a USB-UART adapter.

## External hardware

- Logic analyzer or USB-UART adapter for observing protocol pins
- Pull-up resistors (e.g. 4.7 kOhm) on I2C SDA and SCL
- Optional: I2C/SPI sensor modules for real protocol tests
