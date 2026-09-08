# Lattice MachXO2-1200HC FPGA Core Board

A compact 16-pin FPGA core board based on the **Lattice MachXO2-1200HC**, designed for FPGA learning, digital logic experiments, prototyping, and embedded system development.

The board integrates the FPGA, a 12 MHz clock, USB programming interface, UART communication, power regulation, and status LEDs into a small module with 14 general-purpose I/O pins.

It can be used as a standalone FPGA core module or combined with external circuits and expansion boards for more advanced projects.

## Features

- Lattice MachXO2-1200HC FPGA
- 1,280 LUTs
- 64 Kbits embedded RAM
- One PLL
- Built-in dual-boot configuration Flash
- Two hardware I2C interfaces
- One hardware SPI interface
- One timer
- 14 general-purpose I/O pins
- 12 MHz onboard clock
- Micro-USB power and programming
- DAPLink-based FPGA configuration
- UART communication
- 3.3 V operation
- Onboard power and FPGA status LEDs
- Onboard 5 V to 3.3 V regulator
- Up to 150 mA available from the 3.3 V output pin

## FPGA

The board uses the following device:

**LCMXO2-1200HC-4SG32C**

| Specification | Value |
| --- | --- |
| FPGA family | Lattice MachXO2 |
| Device | LCMXO2-1200HC-4SG32C |
| LUTs | 1,280 |
| Embedded RAM | 64 Kbits |
| PLL | 1 |
| Hardware I2C | 2 |
| Hardware SPI | 1 |
| Timer | 1 |
| Configuration | Built-in dual-boot Flash |
| Supply voltage | 3.3 V |
| External clock | 12 MHz |
| GPIO | 14 |

The FPGA also supports DDR, DDR2, and PDDR functions.

## Board Interfaces

### USB

The board is powered through **Micro-USB**.

The onboard interface supports:

- DAPLink-based FPGA programming
- UART communication
- USB power

Generated FPGA programming files can be transferred through the USB programming interface.

### Clock

A **12 MHz external clock** is provided on the board.

The FPGA's internal PLL can be used when higher internal clock frequencies are required by the design.

### GPIO

The module provides **14 general-purpose I/O pins**.

One GPIO is shared with the onboard FPGA status LED and associated circuitry.

### LEDs

Two LEDs are provided:

- **PWR** — 3.3 V power indicator
- **HB** — FPGA logic/status indicator

The HB LED can be controlled by FPGA logic and is useful for simple tests such as a first blink design.

## 16-Pin Interface

| Module Pin | FPGA Pin | Reference Function |
| --- | ---: | --- |
| 1 - DIO_0 | 8 | OLED_DC |
| 2 - DIO_1 | 9 | OLED_RST |
| 3 - DIO_2 | 10 | OLED_SDA |
| 4 - DIO_3 | 11 | OLED_SCK |
| 5 - DIO_4 | 12 | KEY_4 |
| 6 - DIO_5 | 13 | KEY_3 |
| 7 - DIO_6 | 14 | KEY_2 |
| 8 - DIO_7 | 16 | KEY_1 |
| 9 - DIO_8 | 17 | ADC_PWM |
| 10 - DIO_9 | 25 | Comp_Out |
| 11 - DIO_10 | 23 | PWM_AWG |
| 12 - DIO_11 | 21 | PWM_DC2 |
| 13 - DIO_12 | 20 | PWM_DC1 |
| 14 - DIO_13 / LED | 27 | Shared with onboard LED circuitry |
| 15 - GND | — | Ground |
| 16 - 3.3V | — | 3.3 V supply |

The function names above correspond to the reference pocket-instrument expansion board. The GPIO pins can be assigned to other functions in your own FPGA designs.

The 3.3 V output on pin 16 can supply up to **150 mA** to external circuitry.

## Development Environment

The board can be developed using **Lattice Diamond**.

When creating a project, select:

```text
LCMXO2-1200HC-4SG32C
```

The reference documentation uses **Verilog HDL**, although the normal Lattice FPGA design flow can be used for compatible projects.

A typical development workflow is:

1. Create a new project in Lattice Diamond.
2. Select `LCMXO2-1200HC-4SG32C`.
3. Add your Verilog HDL design files.
4. Synthesize the design.
5. Assign the FPGA pins.
6. Run mapping and place-and-route.
7. Export the JEDEC programming file.
8. Program the board through USB.

## Programming the FPGA

After a successful build, Lattice Diamond generates a `.jed` programming file.

Connect the board to your computer using a USB data cable.

The programming interface appears as a USB mass-storage device named:

```text
STEP FPGA
```

Locate the generated `.jed` file in the project's implementation directory and copy it to the **STEP FPGA** drive.

After the file is copied, the USB device re-enumerates and FPGA programming is complete.

## Reference Expansion Board

The original documentation also describes a **Simple Pocket Instrument DIY Kit** built around this FPGA core module.

The expansion board adds:

- 128 × 64 monochrome OLED display
- Four user-programmable push buttons
- Two adjustable voltage outputs
- DDS arbitrary waveform generator
- Voltmeter function
- Frequency counter

These functions belong to the reference expansion board and are **not all integrated into the FPGA core module itself**.

The reference design demonstrates applications including SPI display control, button debouncing, PWM, DDS, ADC concepts, digital filtering, and frequency measurement.

## Example Applications

The FPGA core board can be used for:

- FPGA and Verilog learning
- Digital logic experiments
- GPIO control
- SPI and I2C experiments
- UART communication
- OLED display control
- PWM generation
- Frequency measurement
- Digital signal processing experiments
- Electronics education
- FPGA prototyping

## Documentation

Detailed documentation is available in the [`Documentation`](Documentation/) directory.

The documentation includes:

- FPGA core board specifications
- Board layout and block diagrams
- Pin mapping
- Lattice Diamond setup
- Project creation
- Verilog design examples
- Pin assignment
- Synthesis and implementation
- JEDEC file generation
- USB programming
- OLED display example
- Push-button example

## Repository Structure

```text
.
├── Detailed-images/    Product and board images
├── Documentation/      Manuals and technical documentation
└── README.md
```

## Getting Started

For a first FPGA project:

1. Connect the board to your computer with a Micro-USB data cable.
2. Install and configure Lattice Diamond.
3. Create a new project for `LCMXO2-1200HC-4SG32C`.
4. Create or add a Verilog HDL design.
5. Assign the required FPGA pins.
6. Synthesize and implement the design.
7. Generate the JEDEC file.
8. Copy the `.jed` file to the `STEP FPGA` USB drive.

See the documentation in this repository for the complete step-by-step development procedure.
