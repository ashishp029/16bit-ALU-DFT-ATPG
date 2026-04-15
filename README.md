# 16-bit ALU DFT and ATPG Flow (Cadence Genus + Modus)

## README.md

````markdown
# 16-bit ALU DFT and ATPG Automation using Cadence Genus & Modus

This project implements a *16-bit ALU design-for-test (DFT) flow* using **Cadence Genus** for synthesis + scan insertion and **Cadence Modus** for ATPG and scan verification.

The repository demonstrates a complete **RTL → synthesized netlist → scan insertion → ATPG vector generation → simulation validation** flow.

---

## 📌 Project Overview
The project includes:
- RTL design of **16-bit ALU** in Verilog
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

## 📂 Repository Structure
```text
.
├── alu_16bit.v
├── alu_16bit.sdc
├── run_genus_dft_alu.tcl
├── run_modus_atpg_alu.tcl
├── runmodus.atpg.tcl
├── run_fullscan_sim
├── run_fullscan_sim_sdf
├── alu_16bit_pre_dft.v
├── alu_16bit_post_dft.v
├── alu_16bit.test_netlist.v
├── pre_dft_*.rpt
├── post_dft_*.rpt
├── dft_rules_check.rpt
├── scan_chains.rpt
├── results/
└── README.md
````

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

## 📊 Important Reports

* `pre_dft_timing.rpt` → Timing before scan insertion
* `post_dft_timing.rpt` → Timing after scan insertion
* `scan_chains.rpt` → Scan chain details
* `test_coverage.rpt` → ATPG fault coverage
* `verify_structures.rpt` → Test structure validation

---

## ✅ Results

* Successful scan insertion
* ATPG vectors generated
* Fault coverage report available
* Simulation verified

