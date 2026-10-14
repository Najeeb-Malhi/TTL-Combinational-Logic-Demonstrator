# TTL-Based Combinational Logic Function Demonstrator

A small hardware project built using 74xx-series TTL logic ICs to explore and implement combinational Boolean logic.

The project started with the 74151 as a conventional 8-to-1 multiplexer and was then extended to demonstrate Boolean-function implementation using a multiplexer, a 3-to-8 decoder, and logic gates.

## Project Overview

The project demonstrates two approaches to implementing combinational logic:

1. **74151 8-to-1 Multiplexer**
   - Basic 8:1 multiplexing
   - Boolean function implementation by programming the data inputs
   - Implementation and verification of a 3-input XOR function
   - Implementation and verification of a 3-input majority function

2. **74138 Decoder + 7408 AND Gates**
   - 3-to-8 decoding
   - Understanding active-low decoder outputs
   - Combining decoder outputs using AND gates
   - Hardware verification of the resulting Boolean function

The circuits were implemented and tested on a digital logic trainer board.

---

## Components Used

| IC | Function |
|---|---|
| 74151 | 8-to-1 Multiplexer |
| 74138 | 3-to-8 Active-Low Decoder |
| 7408 | Quad 2-Input AND Gate |

Additional hardware:

- Digital logic trainer board
- Built-in switches
- Built-in LEDs
- Jumper wires
- 5V TTL logic supply provided by the trainer

---

# Part 1 — 74151 Multiplexer

## 1. Basic 8-to-1 Multiplexer

The 74151 was first tested as a conventional 8-to-1 multiplexer.

Three select inputs determine which of the eight data inputs is transferred to the output.

The general operation is:

```text
S2 S1 S0 = 000  →  I0
S2 S1 S0 = 001  →  I1
S2 S1 S0 = 010  →  I2
S2 S1 S0 = 011  →  I3
S2 S1 S0 = 100  →  I4
S2 S1 S0 = 101  →  I5
S2 S1 S0 = 110  →  I6
S2 S1 S0 = 111  →  I7
```

The selected value appears at the 74151 output.

### 74151 Pin Connections

| Function | Pin |
|---|---:|
| I0 | 4 |
| I1 | 3 |
| I2 | 2 |
| I3 | 1 |
| I4 | 15 |
| I5 | 14 |
| I6 | 13 |
| I7 | 12 |
| S0 | 11 |
| S1 | 10 |
| S2 | 9 |
| Z | 5 |
| Enable | 7 |
| GND | 8 |
| VCC | 16 |

The enable input was held LOW to enable the multiplexer.

---

## 2. Implementing a 3-Input XOR

After verifying the basic multiplexer operation, the 74151 was used to implement a Boolean function.

For:

```text
F = A ⊕ B ⊕ C
```

the data inputs were programmed according to the truth table:

| S2 | S1 | S0 | F |
|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 0 | 1 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 0 |
| 1 | 1 | 1 | 1 |

Therefore:

```text
I0 I1 I2 I3 I4 I5 I6 I7
 0  1  1  0  1  0  0  1
```

The output was verified against all eight input combinations.

---

## 3. Implementing a 3-Input Majority Function

The same 74151 was then reprogrammed to implement a majority function:

```text
F = AB + AC + BC
```

The output is HIGH when at least two of the three inputs are HIGH.

The required data pattern was:

```text
I0 I1 I2 I3 I4 I5 I6 I7
 0  0  0  1  0  1  1  1
```

The resulting output was verified against the corresponding truth table.

This demonstrates that the 74151 can be used not only as a multiplexer, but also as a practical method for implementing Boolean functions.

---

# Part 2 — 74138 Decoder + 7408 Logic

## 1. 74138 as a 3-to-8 Decoder

The 74138 was configured as a 3-to-8 active-low decoder.

Three input variables were applied to the decoder:

```text
C B A
```

The decoder activates one of its eight outputs for each input combination.

Because the outputs are active-low, the selected output becomes LOW while the remaining outputs remain HIGH.

### 74138 Enable Configuration

```text
G2A → LOW
G2B → LOW
G1  → HIGH
```

### 74138 Pin Connections

| Function | Pin |
|---|---:|
| A | 1 |
| B | 2 |
| C | 3 |
| G2A | 4 |
| G2B | 5 |
| G1 | 6 |
| Y7 | 7 |
| GND | 8 |
| Y6 | 9 |
| Y5 | 10 |
| Y4 | 11 |
| Y3 | 12 |
| Y2 | 13 |
| Y1 | 14 |
| Y0 | 15 |
| VCC | 16 |

The decoder outputs were initially observed using the trainer-board LEDs.

---

## 2. 74138 + 7408 Logic Function

The decoder was then combined with a 7408 quad 2-input AND gate.

The selected decoder outputs:

```text
Y0, Y1, Y4, Y5
```

were combined using three 2-input AND gates inside the 7408 to construct a 4-input AND function.

### 7408 Connections

First AND gate:

```text
Y0 → pin 1
Y1 → pin 2
Output → pin 3
```

Second AND gate:

```text
Y4 → pin 4
Y5 → pin 5
Output → pin 6
```

Third AND gate:

```text
pin 3 → pin 9
pin 6 → pin 10
Final output → pin 8
```

The final output was connected to a trainer-board LED.

The 7408 was powered using:

```text
VCC → pin 14
GND → pin 7
```

---

## 3. Decoder-Based Function Verification

The resulting function was verified using all eight combinations of the three input variables.

| C | B | A | F |
|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 1 |
| 1 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |
| 1 | 1 | 1 | 1 |

The hardware output matched the expected truth table.

---

# Project Architecture

The project can be summarized as two different approaches to combinational logic:

```text
                 3-Input Logic
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
          74151              74138
        8:1 MUX            3:8 Decoder
             │                 │
             │              Active-Low
             │               Outputs
             │                 │
             │                 ▼
             │               7408
             │             AND Gates
             │                 │
             ▼                 ▼
          Boolean          Boolean
          Function         Function
```

---

# Key Concepts Learned

- 8-to-1 multiplexing
- 3-to-8 decoding
- Active-low logic
- Boolean function implementation using multiplexers
- Truth-table based circuit design
- Minterm-based logic implementation
- Cascading multiple logic gates to create larger logic functions
- Practical TTL circuit wiring and debugging
- Hardware verification of theoretical truth tables

---

# Project Photos

### 74151 Multiplexer

![74151 Multiplexer](images/01-74151-multiplexer.jpg)

### 74138 Decoder

![74138 Decoder](images/02-74138-decoder.jpg)

### Final 74138 + 7408 Logic Circuit

![Final Logic Circuit](images/03-final-combinational-logic.jpg)

---

# Future Work

This project is part of my progression toward larger digital hardware systems.

Planned future projects include:

- 4-bit arithmetic circuits
- 4-bit ALU
- Registers and counters
- Memory interfacing
- Larger-scale TTL logic systems
- Eventually, an 8-bit CPU

---

## Author

**Muhammad Najeeb**

Computer Engineering Student  
UET Lahore

---

## License

This project is intended primarily for educational and learning purposes.