# Common Bus System using 4-bit Multiplexers (Logisim)

## Overview

This project implements a **Common Bus System** using **4-bit multiplexers (MUXes)** in Logisim. The design allows multiple registers to share a single communication pathway (bus), enabling controlled data transfer between registers.

The bus system is a fundamental concept in computer architecture, commonly used in CPU datapaths and digital systems.

---

## Features

* 4-bit wide common bus
* Multiple registers connected to a shared bus
* Selection of source register using control lines
* Synchronous data transfer using clocked registers
* Modular and scalable design

---

## Components Used

* 4-bit Registers (with Load/Write Enable)
* 4-to-1 Multiplexers (4-bit wide)
* Clock source
* Control switches (for select lines)
* Input/Output pins or LEDs for visualization
* Splitters and tunnels (optional for clean wiring)

---

## Architecture

### Bus Design

The common bus is implemented using **4 multiplexers**, one for each bit:

* Each MUX selects one bit from corresponding bits of all registers
* Outputs of all MUXes together form the 4-bit bus

### Register Set

* 4 registers (R0, R1, R2, R3), each 4 bits wide
* Each register has:

  * Data input (connected to bus)
  * Write Enable (WE)
  * Clock input

### Selection Lines

* 2-bit select lines (S1, S0)
* These control which register is placed onto the bus

| S1 | S0 | Selected Register |
| -- | -- | ----------------- |
| 0  | 0  | R0                |
| 0  | 1  | R1                |
| 1  | 0  | R2                |
| 1  | 1  | R3                |

---

## How It Works

1. **Selecting a Register to Output**

   * Use the select lines (S1, S0) to choose which register places its value on the bus.

2. **Bus Operation**

   * The selected register’s 4-bit output is routed through the multiplexers onto the common bus.

3. **Writing to a Register**

   * Enable the Write Enable (WE) of the destination register.
   * On the clock edge, the value on the bus is stored into that register.

---

## Steps to Run in Logisim

1. Open the `.circ` file in Logisim.
2. Ensure the clock is connected and running (manual or automatic).
3. Set the select lines (S1, S0) using input switches.
4. Observe the bus output via LEDs or probes.
5. Enable a register’s WE to load data from the bus.
6. Toggle the clock to complete the write operation.

---

## Example Operation

**Transfer data from R1 to R3:**

1. Set select lines to `01` (select R1).
2. Enable WE for R3.
3. Pulse the clock.
4. R3 now contains the value previously in R1.

---

## Notes

* Only one register should drive the bus at a time (handled by MUX selection).
* Avoid enabling multiple writes unintentionally.
* The design can be extended to more registers by increasing MUX inputs and select lines.

---

## Future Improvements

* Expand to 8-bit or 16-bit bus
* Add ALU integration
* Include control unit for automation
* Implement tri-state buffer-based bus alternative

---

## License

This project is for educational use.
