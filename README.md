# 4-Bit & 8-Bit Digital Calculator — DLD Semester Project
**Group Members:** Rameen Fatima | Aizah Atif 

---

##  Project Overview

This project implements a digital calculator in two versions:

| Version | Implementation |
|---------|---------------|
| **4-bit** | Built physically on breadboard using discrete ICs + simulated in Proteus |
| **8-bit** | Simulated in Proteus only |

Both versions perform the same arithmetic and logic operations, with the 8-bit extending the data width for larger values. The 4-bit calculator also displays results in decimal on **7-segment displays** using a custom binary-to-BCD converter.

This project brings digital logic theory to life — from Proteus simulation to real physical hardware.

---

##  Operations Supported

| Operation | Logic Used |
|-----------|-----------|
| Addition  | 74LS83 4-bit Full Adder |
| Subtraction | 7404 (B inversion) + 74LS83 |
| Multiplication | 7408 AND gates + 74LS83 |
| AND | 7408 |
| OR  | 7432 |
| XOR | 7486 |
| NOT A / NOT B | 7404 + 74157 MUX selector |

---

##  Components Used

| IC / Component | Function |
|----------------|----------|
| 74LS83 | 4-bit Full Adder |
| 7404 | NOT Gate |
| 7408 | AND Gate |
| 7432 | OR Gate |
| 7486 | XOR Gate |
| 74157 | 2:1 MUX (NOT selector) |
| 74151 | 8:1 MUX (ALU & output selection) |
| 74LS138 | 3-to-8 Line Decoder (BCD routing) |
| 7447 | BCD to 7-Segment Decoder |
| 5161AS | 7-Segment Common Cathode Display (×2) |
| Breadboard, DIP Switches, Jumper Wires, LEDs, Resistors (220Ω) |

**Total component cost:** ~PKR 20,000–25,000 (sourced from College Road, Saddar, Rawalpindi)

---

##  Binary-to-BCD Conversion (Double Dabble / Shift-Add-3)

The final 4-bit ALU output is converted to BCD for display using the **shift-add-3 algorithm**, implemented entirely from discrete logic (not a single BCD IC):

- Detects when a 4-bit group ≥ 5 using: `GreaterThanFive = A3 OR (A2 AND A1) OR (A2 AND A0)`
- Adds 3 to that group via custom conditional adders (74LS83 + 74157 + AND/OR gates)
- Routes each BCD digit to a **7447 decoder → 5161AS 7-segment display**

---

## Repository Structure

```
📦 DLD-Calculator-Project
├── 📄 README.md
├── 📄 24i-0782_24i-0840_DLDPROJECT_HARDWAREREPORT.docx   # Full project report
└── 📂 Proteus/
    ├── 24i-0782_24i-0840_4BIT.pdsprj    # 4-bit Proteus simulation
    └── 24i-0782_24i-0840_8BIT.pdsprj    # 8-bit Proteus simulation
```
---

##  Challenges & Lessons Learned

- **Overheating ICs:** 74153 and 7408 overheated during testing. Replaced with 8:1 MUXes and powered off between tests.
- **MUX Routing Issues:** Took 2 days of step-by-step tracing with LEDs to rebuild and verify the multiplexer block.
- **Loose Connections:** Used color-coded wires and staple pins for cleaner, more stable wiring.
- **Unstable Inputs:** Grounded all unused IC inputs through 220Ω resistors to fix erratic behavior.

---
## Conclusion
The project successfully implements a digital calculator in both 4-bit (physical + simulated) and 8-bit (simulated) forms. Going from Proteus simulation to real breadboard hardware demonstrated practical skills in wiring, logic analysis, and digital system troubleshooting — while the 8-bit extension deepened our understanding of scalable ALU design.
