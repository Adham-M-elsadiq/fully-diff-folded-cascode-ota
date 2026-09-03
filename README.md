# Fully-Differential Folded Cascode OTA Design

This repository contains the design, simulation, and verification files for a Fully-Differential Folded Cascode Operational Transconductance Amplifier (OTA) with capacitive feedback. The circuit is implemented in the **GF180MCU** technology node.

This project was developed as part of the Analog IC Design course (Lab 11 - Mini Project 02).

## Directory Structure

*   **`docs/`**: Project documentation.
    *   `Folded_Cascode_OTA Report.pdf`: The comprehensive final lab report detailing the design procedure, analytical calculations, and simulation results.
    *   `hand_analysis.pdf`: Detailed theoretical hand calculations.
    *   `aic_lab_cadence_mm_11_folded_v01.pdf`: Original project specifications and lab manual.
    *   `images/`: Miscellaneous schematics and circuit reference images.
*   **`simulations/`**: Contains simulation results, figures, and data grouped by design phase.
    *   `part1_gmid_charts/`: $g_m/I_D$ device characterization charts (VA, fT, W/ID, VGS).
    *   `part3_open_loop_behavioral_cmfb/`: DC and AC simulations with an ideal behavioral CMFB.
    *   `part4_open_loop_actual_cmfb/`: DC and AC simulations using the transistor-level CMFB circuit.
    *   `part5_closed_loop_ac_stb/`: Closed-loop AC and Stability (STB) analysis for both Differential and CMFB loops.
    *   `part6_closed_loop_transient/`: Transient analysis (settling time, CM step response, and large-signal sine test).
    *   `schematics_and_testbenches/`: *(Reserved for future Cadence Schematic and Testbench database files)*
*   **`layout/`**: *(Reserved for future layout views and physical verification)*
*   **`scripts/`**: *(Reserved for future automation scripts)*

## Design Specifications & Achievements (GF180MCU, 2.5V)

The design successfully meets and exceeds all targeted specifications:

| Parameter | Target Spec (2.5V) | Achieved (Simulated) |
| :--- | :--- | :--- |
| **Supply Voltage** | 2.5 V | 2.5 V |
| **Closed-loop gain** | 2 V/V | 1.998 V/V |
| **Phase margin @ ACL** | $\ge 70^\circ$ | $89.28^\circ$ |
| **CM input range – low** | $\le 0$ V | 0 V |
| **CM input range – high**| $\ge 1$ V | 1.486 V |
| **Differential output swing** | 1.2 V peak-to-peak | 1.199 V peak-to-peak |
| **Load capacitance** | 500 fF | 500 fF |
| **DC loop gain** | 60 dB | 62.24 dB |
| **CL settling time (1% error)** | 100 ns | 98.19 ns |

## Design Methodology

The sizing procedure heavily utilizes the **$g_m/I_D$ methodology** using ADT Sizing Assistant lookup tables.
*   The **input differential pair** (PMOS) utilizes minimum length ($L = 370$ nm) to minimize input capacitance and maximize feedback factor ($\beta$).
*   The **bias split ratio** is $S=2$, allocating optimal current to the input pair for higher $G_m$ without overly sacrificing the non-dominant pole.
*   The **CMFB network** employs PMOS source followers to sense the output without resistive loading, followed by a low-gain error amplifier to maintain high-frequency loop stability.

## How to use this repository
*   Read `docs/Folded_Cascode_OTA Report.pdf` for a complete walkthrough of the design choices and trade-offs.
*   Simulation figures are categorized in `simulations/` based on the steps outlined in the report.
*   Cadence database files (schematics/symbols) will be added to `simulations/schematics_and_testbenches/` at a later stage.
