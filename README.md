# MOSFETs and BJTs Analysis

## Overview

This repository contains the complete analysis of **ECE335 Lab 3**, investigating the electrical characteristics and extracting key device parameters from MOSFET and BJT technologies. The lab combines in-lab measurements of planar MOSFETs with computational analysis of advanced nanoscale devices (FDSOI and finFET) and commercial BiCMOS BJT technologies.

## Project Structure

```
Lab-3-MOSFETs-and-BJTs/
├── Lab3_Analysis.ipynb          # Main analysis notebook with all calculations and plots
├── Lab3_instruction.md          # Lab assignment instructions and specifications
├── Lab3_data.md                 # In-lab measured data (planar NMOS/PMOS)
├── ECE335_MOSFET_data/          # Nanoscale MOSFET measurement data
│   ├── Planar MOSFET/           # 6 channel lengths (65nm - 350nm)
│   └── FDSOI and finFET MOSFET/ # Advanced technology nodes (20nm, 8nm)
└── ECE335_BJT_data/             # BiCMOS HBT frequency response data
```

## Technologies Analyzed

### 1. Planar MOSFETs (In-lab Measurements)
- **Devices**: ALD1101 (n-channel), ALD1102 (p-channel)
- **Channel Lengths**: 65nm, 90nm, 130nm, 180nm, 250nm, 350nm
- **Width**: 1 μm (80 fingers in parallel)

### 2. FDSOI MOSFETs (University of Toronto Data)
- **Technology Node**: 20nm
- **Structure**: Fully-Depleted Silicon-On-Insulator
- **Width**: 40 × 0.43 μm
- **Channels**: Both n-type and p-type

### 3. finFET MOSFETs (University of Toronto Data)
- **Technology Node**: 8nm
- **Structure**: 3D multi-gate (48 fins × 4 fins/finger)
- **Effective Width**: 48 × 4 × 90 nm
- **Channels**: Both n-type and p-type

### 4. BiCMOS BJTs
- **Type**: SiGe npn Heterojunction Bipolar Transistors
- **Technologies**: Three commercial BiCMOS generations
  - b9mw
  - bicmos6g
  - bicmos9

## Key Parameters Extracted

### MOSFET Parameters

| Parameter | Description | Method |
|-----------|-------------|--------|
| **Vt0** | Threshold voltage | Transconductance peak extrapolation |
| **η (DIBL)** | Drain-Induced Barrier Lowering | Threshold shift vs. VDS |
| **λ** | Channel length modulation | Early voltage from output characteristics |
| **k'n** | Process transconductance | Effective channel length analysis |
| **ΔL** | Channel length offset | Linear region slope analysis |
| **ION/W** | On-current density | Maximum current at high VGS, VDS |
| **gm/W** | Transconductance density | Peak transconductance normalized to width |
| **SS** | Subthreshold slope | Inverse slope of log(ID) vs. VGS |
| **tOXE** | Equivalent oxide thickness | C-V characteristics analysis |

### BJT Parameters

| Parameter | Description |
|-----------|-------------|
| **fT** | Unity current gain frequency | Extrapolated from H21 vs. frequency |
| **IC** | Collector current | Operating point for fT extraction |

## Analysis Highlights

### Technology Comparison Results

**Threshold Voltage (Vt0)**:
- Planar 65nm: ~0.47 V
- FDSOI 20nm: ~0.20 V
- finFET 8nm: ~0.19 V
- *Finding*: Advanced nodes show ~58% lower Vt0

**DIBL Performance (η - lower is better)**:
- Planar 65nm: 0.0964
- FDSOI 20nm: 0.1056
- finFET 8nm: 0.0366
- *Finding*: finFET shows 3× better DIBL resistance due to 3D gate control

**Subthreshold Slope (SS - closer to 60 mV/dec is better)**:
- FDSOI: 83.91 mV/dec
- finFET: 65.78 mV/dec
- *Finding*: finFET approaches ideal limit

**Channel Length Modulation (λ)**:
- Extracted from saturation region output conductance
- Negative Early voltages observed due to short-channel effects
- λ = 1/|VA| for advanced technology nodes

## Methodology

### Data Processing Pipeline

1. **Data Import**: Load CSV files for transfer and output characteristics
2. **Vt0 Extraction**: 
   - Calculate gm = dID/dVGS
   - Find peak gm location
   - Linear extrapolation to ID = 0 axis
   - Apply thermal correction: Vt0 = Vintercept - 3kT/q
3. **DIBL Analysis**:
   - Interpolate VGS at constant ID for low/high VDS
   - η = |ΔVGS| / ΔVDS
4. **Performance Metrics**:
   - ION/W at VGS = VDD, VDS = VDD
   - gm/W from peak transconductance
   - SS from subthreshold region: d(log10(ID))/dVGS
5. **C-V Analysis**:
   - Extract Cmax and Cmin from plots
   - Calculate tOXE = ε0εox × A / Cmax

### Unit Conversions

- Current density: 1 A/m = 1 μA/μm (identity)
- Transconductance density: 1 S/m = 0.001 mS/μm
- Resistance: R' = 220 Ω·μm for source/drain contacts

## Tools and Libraries

- **Python 3.x**: Primary analysis environment
- **NumPy**: Numerical computations, gradient calculations
- **Pandas**: CSV data handling
- **Matplotlib**: Visualization (transfer/output characteristics, comparisons)
- **SciPy**: Interpolation for parameter extraction

## Key Findings

1. **Technology Scaling Benefits**:
   - finFET demonstrates superior electrostatic control
   - Reduced DIBL and improved SS compared to planar structures
   - Lower threshold voltages enable lower power operation

2. **Short-Channel Effects**:
   - Negative Early voltages common in advanced nodes
   - Velocity saturation impacts output characteristics
   - DIBL becomes more significant as L decreases

3. **3D vs. Planar Structures**:
   - finFET's multi-gate architecture provides better gate control
   - FDSOI uses thin buried oxide for improved performance
   - Both outperform traditional planar devices

## Validation

All extracted parameters validated for physical reasonableness:
- ✓ Vt0 within expected range for each technology
- ✓ DIBL trends match theoretical predictions
- ✓ SS values approach theoretical minimum
- ✓ Unit conversions verified
- ✓ Results consistent with published literature
