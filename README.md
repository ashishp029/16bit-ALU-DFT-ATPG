# 16-bit ALU DFT and ATPG Flow (Cadence Genus + Modus)

## README.md

````markdown
# 16-bit ALU DFT and ATPG Automation using Cadence Genus & Modus

This project implements a 16-bit ALU design-for-test (DFT) flow using Cadence Genus for synthesis + scan insertion and Cadence Modus for ATPG and scan verification.

The repository demonstrates a complete **RTL → synthesized netlist → scan insertion → ATPG vector generation → simulation validation** flow.

---

## 📌 Project Overview
The project includes:
- RTL design of 16-bit ALU in Verilog
- Synthesis constraints using SDC
- Pre-DFT synthesis reports
- Scan chain insertion
- Post-DFT timing/area/power reports
- ATPG setup and test vector generation
- Full-scan simulation scripts
- Coverage and structure verification reports

This is useful for:
- VLSI DFT lab projects
- Cadence Genus/Modus learning
- ATPG flow understanding
- Scan chain insertion practice
- Academic mini-project / B.Tech project

---

## ⚙️ Tools Used

* **Cadence Genus** → RTL synthesis + DFT insertion
* **Cadence Modus** → ATPG + fault coverage
* **Verilog HDL** → RTL design
* **SDC** → Timing constraints

---

## 🚀 How to Run

### 1) Run synthesis + DFT insertion

```bash
genus run_genus_dft_alu.tcl
```

### 2) Run ATPG

```bash
modus run_modus_atpg_alu.tcl
```

### 3) Run full scan simulation

```bash
./run_fullscan_sim
```

---


---


## 📊 Report Summary Tables (Generated from Actual Reports)

### 1) Timing Comparison (Pre-DFT vs Post-DFT)

| Metric               |               Pre-DFT |              Post-DFT | Observation                        |
| -------------------- | --------------------: | --------------------: | ---------------------------------- |
| Required Time (ps)   |                 19285 |                 19302 | Slight improvement                 |
| Data Path Delay (ps) |                  5857 |                  5992 | Increased due to scan mux overhead |
| Slack (ps)           |                  8428 |                  8311 | Minor reduction after DFT          |
| Timing Status        |                   MET |                   MET | Timing clean in both stages        |
| Critical Endpoint    | `flag_overflow_reg/D` | `flag_overflow_reg/D` | Same critical path                 |

### 2) Scan Chain Summary

| Metric               |                     Value |
| -------------------- | ------------------------: |
| Total Scan Chains    |                         1 |
| Total Scan Bits      |                        19 |
| Longest Chain Length |                        19 |
| Average Chain Length |                        19 |
| Scan Input           |                 `scan_in` |
| Scan Output          |                `scan_out` |
| Status               | Controllable & Observable |

### 3) ATPG / Fault Coverage Results

| Metric                |       Value |
| --------------------- | ----------: |
| Total Static Faults   |        2228 |
| Tested Static Faults  |        2228 |
| Static Coverage       | **100.00%** |
| Dynamic Faults        |        2228 |
| Tested Dynamic Faults |         120 |
| Dynamic Coverage      |       5.39% |
| Logic Patterns        |          57 |
| Scan Patterns         |           1 |
| Total Patterns        |          58 |

### 4) Test Structure Verification

| Metric               |              Value |
| -------------------- | -----------------: |
| Total Flip-Flops     |                 19 |
| Total Cell Instances |                255 |
| Primary Inputs       |                 40 |
| Primary Outputs      |                 21 |
| Scan Enable Pins     |                  1 |
| Scan Input Pins      |                  1 |
| Scan Output Pins     |                  1 |
| Clock Pins           | 2 system + 1 shift |
| Verification Result  |               PASS |

### 5) DFT Quality Summary

| Check                       | Result   |
| --------------------------- | -------- |
| Timing after scan insertion | PASS     |
| Scan chain controllability  | PASS     |
| Scan chain observability    | PASS     |


---

## ✅ Results

* Successful scan insertion
* ATPG vectors generated
* Fault coverage report available
* Simulation verified

| ATPG static coverage        | 100%     |
| Test vector generation      | PASS     |
| Full scan structure         | VERIFIED |

These tables are ideal for your **GitHub README**, **resume project section**, and **project report screenshots**.
