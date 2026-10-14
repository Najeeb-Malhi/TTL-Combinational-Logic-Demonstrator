TTL-Based Combinational Logic Demonstrator

An initial hands-on project in Digital Logic Design, exploring how TTL logic ICs can be used to implement and verify Boolean functions.

Built and tested on a digital logic trainer using the 74151, 74138, and 7408 ICs.

What I Built

- 74151 — 8:1 Multiplexer: Verified multiplexing and implemented a 3-input XOR function and a majority function by configuring the data inputs.
- 74138 — 3:8 Decoder: Explored binary decoding and active-low outputs.
- 7408 — AND Gates: Combined decoder outputs to implement and verify a Boolean function.

Logic Functions Implemented

- 3-input XOR: (F = A \oplus B \oplus C)
- 3-input Majority: (F = AB + AC + BC)
- Decoder-based function: (F = B), implemented using the 74138 and 7408.

All functions were tested against their expected truth tables.

Hardware Setup

The circuits were assembled on a digital logic trainer using its built-in switches and LEDs.

Circuit Photos

74151 Multiplexer

"74151 Multiplexer" (images/01-74151-multiplexer.jpg)

74138 Decoder

"74138 Decoder" (images/02-74138-decoder.jpg)

Decoder-Based Logic — 74138 + 7408

"Final Logic Circuit" (images/03-final-combinational-logic.jpg)

Key Takeaways

- Boolean-function implementation using multiplexers
- Active-low logic and binary decoding
- Combining TTL ICs to build combinational circuits
- Hardware verification using truth tables

What's Next?

Exploring more advanced digital hardware, including arithmetic circuits, ALUs, and eventually CPU design.

---

Built by: Muhammad Najeeb
Computer Engineering Student | UET Lahore