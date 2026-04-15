# 16-bit ALU DFT and ATPG Flow (Cadence Genus + Modus)

## README.md

````markdown
# 16-bit ALU DFT and ATPG Automation using Cadence Genus & Modus

This project implements a **16-bit ALU design-for-test (DFT) flow** using **Cadence Genus** for synthesis + scan insertion and **Cadence Modus** for ATPG and scan verification.

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
genus -f run_genus_dft_alu.tcl
```

### 2) Run ATPG

```bash
modus -f run_modus_atpg_alu.tcl
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

---

## 👨‍💻 Author

**Ashish**
B.Tech VLSI / Digital Design Project

````

---

# ✅ Files You SHOULD Upload to GitHub
These are the **important source + reproducible result files**:

### Core source files
- `alu_16bit.v`
- `alu_16bit.sdc`
- `run_genus_dft_alu.tcl`
- `run_modus_atpg_alu.tcl`
- `runmodus.atpg.tcl`
- `run_fullscan_sim`
- `run_fullscan_sim_sdf`

### Important generated netlists
- `alu_16bit_pre_dft.v`
- `alu_16bit_post_dft.v`
- `alu_16bit.test_netlist.v`

### Useful reports
- `pre_dft_*.rpt`
- `post_dft_*.rpt`
- `dft_rules_check.rpt`
- `scan_chains.rpt`
- `results/test_coverage.rpt`
- `results/verify_structures.rpt`
- `results/test_structures.rpt`

### Optional academic proof files
- `alu_16bit.scandef`
- `alu_16bit_post_dft.sdf`
- `alu_16bit_post_dft.sdc`

---

# ❌ Files/Folders You should NOT Upload
These are tool-generated temporary/cache files:

- `tbdata/`
- `testresults/`
- `fv/`
- `*.log`
- `*.cmd`
- `.rs_*`
- `*.tstamp`
- lock files
- Cadence internal database files

These make repo **huge and messy**.

---

# ✅ Recommended .gitignore
```gitignore
# Cadence temporary data
tbdata/
testresults/
fv/
results/*.tmp

# Logs
*.log
*.cmd
*.tstamp
.rs_*

# Generated databases
*.db
*.dat
*.lock
````

---

# ⭐ Best GitHub Upload Strategy

Upload only:

1. RTL
2. TCL scripts
3. SDC
4. Important reports
5. Final post-DFT netlist
6. README.md

This makes your GitHub look **professional and recruiter-friendly**.

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
| ATPG static coverage        | 100%     |
| Test vector generation      | PASS     |
| Full scan structure         | VERIFIED |

These tables are ideal for your **GitHub README**, **resume project section**, and **project report screenshots**.
