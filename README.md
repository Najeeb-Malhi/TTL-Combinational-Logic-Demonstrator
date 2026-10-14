
# TTL-Based Combinational Logic Function Demonstrator

An initial hands-on Digital Logic Design project exploring Boolean logic implementation using 74xx-series TTL ICs.

## Project Overview

Built and tested on a digital logic trainer using three ICs:

| IC | Function |
|---|---|
| 74151 | 8:1 Multiplexer |
| 74138 | 3:8 Active-Low Decoder |
| 7408 | Quad 2-Input AND Gate |

## Implemented Functions

### 1. 74151 — Multiplexer-Based Logic
- Verified basic 8:1 multiplexing.
- Implemented and verified 3-input XOR: `F = A ⊕ B ⊕ C`
- Implemented and verified 3-input majority: `F = AB + AC + BC`

### 2. 74138 + 7408 — Decoder-Based Logic
- Verified 3-to-8 decoding and active-low outputs.
- Combined decoder outputs using three AND gates to implement a Boolean function.
- Verified the output against all eight input combinations.

## Hardware Setup

The circuits were assembled using a digital logic trainer's built-in switches and LEDs.

## Project Photos

### 74151 Multiplexer
![74151 Multiplexer](images/01-74151-multiplexer.jpg)

### 74138 Decoder
![74138 Decoder](images/02-74138-decoder.jpg)

### Combined Decoder and Logic Gates
![Final Logic Circuit](images/03-final-combinational-logic.jpg)

## Key Learnings

- Boolean-function implementation using multiplexers
- Binary decoding and active-low logic
- Combining TTL ICs to build combinational circuits
- Hardware testing using truth tables

## Future Work

Exploring arithmetic circuits, ALUs, and eventually 8-bit CPU design.

---

**Author:** Muhammad Najeeb  
Computer Engineering Student | UET Lahore
