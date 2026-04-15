# 16-bit ALU with DFT Insertion and ATPG using Cadence Genus + Modus

This project implements a **16-bit ALU in Verilog**, followed by:

- RTL synthesis using **Cadence Genus**
- **DFT scan insertion**
- **Single scan chain generation**
- ATPG using **Cadence Modus**
- Fault coverage and structural test report generation

This project demonstrates a complete **RTL-to-DFT-to-ATPG flow** used in VLSI design verification.

---

## 📌 Features

### ✅ Functional ALU Operations
The 16-bit ALU supports 8 operations:

| Opcode | Operation |
|---|---|
| 000 | ADD |
| 001 | SUB |
| 010 | AND |
| 011 | OR |
| 100 | XOR |
| 101 | NOT |
| 110 | Shift Left |
| 111 | Shift Right |

### ✅ Status Flags
- Zero
- Carry
- Overflow
- Negative

### ✅ DFT Features
- Muxed scan architecture
- `scan_en`
- `scan_in`
- `scan_out`
- Single scan chain
- Full scan compatible

---

## 📂 Project Structure

```text
├── alu_16bit.v                     # RTL design
├── alu_16bit.sdc                  # Timing constraints
├── run_genus_dft_alu.tcl          # Genus synthesis + DFT script
├── run_modus_atpg_alu.tcl         # Modus ATPG script
│
├── reports/
│   ├── pre_dft_area.rpt
│   ├── pre_dft_power.rpt
│   ├── pre_dft_timing.rpt
│   ├── post_dft_area.rpt
│   ├── post_dft_power.rpt
│   ├── post_dft_timing.rpt
│   ├── scan_chains.rpt
│   └── dft_setup.rpt
│
├── results/
│   ├── test_coverage.rpt
│   ├── test_structures.rpt
│   └── verify_structures.rpt
│
└── tbdata/                        # Modus generated ATPG database
```

---

## ⚙️ Tools Used

- **Verilog HDL**
- **Cadence Genus**
- **Cadence Modus**
- **TCL scripting**
- **90nm Standard Cell Library**

---

## 🚀 Flow Used

### 1️⃣ RTL Design
The ALU is written in Verilog with scan-compatible registers.

### 2️⃣ Synthesis
Using Cadence Genus:
- RTL elaboration
- Logic synthesis
- Constraint-driven optimization

### 3️⃣ DFT Insertion
- Scan replacement
- Scan chain stitching
- DFT rule checks
- Scan chain reports

### 4️⃣ ATPG
Using Cadence Modus:
- Fault model generation
- Stuck-at ATPG
- Pattern generation
- Coverage report

---

## 📊 Sample Results

### Pre-DFT Reports
- Timing
- Area
- Power
- Gate count

### Post-DFT Reports
- Scan overhead
- Area increase
- Timing impact
- DFT validation

### ATPG Reports
- Fault coverage
- Structural verification
- Pattern quality

---

## 🎯 Learning Outcomes

This project helped in understanding:

- RTL design methodology
- Scan insertion flow
- DFT rule checks
- ATPG pattern generation
- Fault coverage analysis
- TCL automation for EDA tools

---

## 👨‍💻 Author
**Ashish**  
B.Tech Electronics / VLSI / Digital Design

---
