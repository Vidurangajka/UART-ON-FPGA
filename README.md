# UART Interface on DE-Nano-2 FPGA

This project implements a simple UART (Universal Asynchronous Receiver/Transmitter) on the DE-Nano-2 FPGA development board based on the Intel MAX10 FPGA.

## 📦 Project Contents

- `uart_tx.v` — UART transmitter module (Verilog)
- `uart_rx.v` — UART receiver module (Verilog)
- `baud_generator.v` — Clock divider for baud rate generation
- `top.v` — Top-level integration file
- `uart_testbench.v` — Testbench for simulation
- `README.md` — This documentation
- `*.qsf` — Quartus project and pin assignment file
- `*.sdc` — Timing constraint file

## 🛠 Requirements

- [Intel Quartus Prime (Lite Edition)](https://www.intel.com/content/www/us/en/software/programmable/quartus-prime/download.html)
- [ModelSim Intel FPGA Edition](https://www.intel.com/content/www/us/en/software/programmable/modelsim.html) (optional for simulation)
- DE-Nano-2 FPGA Board
- USB-to-UART module (CP2102, FTDI, etc.)
- Serial terminal (e.g., TeraTerm, PuTTY)

## 🔧 Hardware Connections

| FPGA Pin | UART Function | Description        |
|----------|----------------|--------------------|
| GPIO_0   | TX             | Transmit to PC     |
| GPIO_1   | RX             | Receive from PC    |
| GND      | GND            | Common ground      |

> Pin names (e.g., GPIO_0) must be mapped according to your board layout and `.qsf` file.

## ⚙️ Baud Rate Generator

The baud generator uses the system clock (e.g., 50 MHz) to create timing for UART (e.g., 9600 bps).

You can configure this in `baud_generator.v`:

```verilog
parameter CLOCK_FREQ = 50000000; // 50 MHz
parameter BAUD_RATE  = 9600;
