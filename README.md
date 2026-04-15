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

The following synthesis, DFT, and ATPG results were obtained from **Cadence Genus and Modus reports** included in this repository.

---

### 🔹 Pre-DFT vs Post-DFT Synthesis Comparison

| Metric | Pre-DFT | Post-DFT | Impact |
|---|---:|---:|---:|
| Cell Count | 247 | 253 | +6 |
| Total Area | 1708.323 | 1813.532 | **+6.16%** |
| Total Power (W) | 5.68121e-05 | 6.44671e-05 | **+13.47%** |
| Worst Setup Slack (ps) | 8428 | 8311 | **-117 ps** |
| Scan Flip-Flops | DFFRHQX1 / DFFRHQX2 | **SDFFRHQX1 = 17** | Scan inserted ✅ |

---

### 🔹 DFT / Scan Chain Results

| Parameter | Result |
|---|---|
| DFT Style | Full Scan |
| Scan Architecture | Muxed Scan |
| Scan Chains | 1 |
| Scan FF Type | SDFFRHQX1 |
| Scan Overhead | 6 extra cells |
| DFT Rule Check | Passed |
| Scan Chain Stitching | Successful |

---

### 🔹 ATPG Results (Cadence Modus)

| Parameter | Value |
|---|---:|
| Total Static Faults | 2228 |
| Total Dynamic Faults | 2148 |
| Detected Faults (1st pattern set) | 159 |
| Untested Faults | 2069 |
| Test Coverage | **7.14%** |
| Adjusted Coverage | **7.14%** |
| Test Mode | FULLSCAN |

---

### 🔹 Key Observations

- **Area increased by 6.16%** after scan insertion
- **Power overhead increased by 13.47%**
- Timing degradation is minimal (**117 ps slack reduction**)
- Full-scan DFT insertion successfully replaced normal FFs with **scan FFs**
- Initial ATPG run achieved **7.14% fault coverage**
- Further pattern optimization can improve coverage significantly

---

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
**Ashish Prajapati**  
IIITDM Kurnool / B.Tech / Electronics and Communication Engineering / VLSI 

---
