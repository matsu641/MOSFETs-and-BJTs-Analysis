# ECE335 Introduction to Electronic Devices

**LAB 3**

# ECE335 Introduction to Electronic Devices

## Lab 3 – MOSFETs and BJTs

*Edward S. Rogers Sr. Department of Electrical and Computer Engineering*
*University of Toronto*

**Last Revised: Sept. 2025**

---

## 1 Introduction

This lab has two parts. Part 1 is an in-lab measurement and part 2 is a take-home lab. You measure the IV characteristics of **n-channel and p-channel MOSFETs** to extract the major model parameters from standard DC measurements. Then you use numerical methods to analyze supplied data of nanoscale planar, FDSOI and finFET MOSFETs which are previously measured at the **University of Toronto**. From the data, you investigate the IV characteristics and extract the threshold voltage (Vₜ), DIBL parameter (η), channel modulation parameter (λ), and electron mobility (μₙ), then compare the devices. Next, you are provided with data of BJT devices previously measured at the **University of Toronto**. You will extract the fₜ vs. Ic characteristics of four SiGe npn Heterojunction Bipolar Transistors fabricated in four different generations of commercial SiGe BiCMOS technologies. Post-lab and pre-lab questions are to be completed in your lab groups. Submit the post lab as a PDF to Quercus. 20 marks for post lab analysis, 3 marks pre-lab, 2 marks for attendance.

---

## 2 Objectives

* To measure the IV characteristics of planar **n-MOSFET** and **p-MOSFET**
* To compare the measured IV characteristics of planer MOSFETs, FDSOI, and finFET MOSFETs.
* To learn how to extract the DC compact model parameters of MOSFETs.
* To learn how to extract **fₜ** of different BJT devices

---

## 3 Background

* MOS Capacitor and MOSFET (Ch. 9—11, Neamen)
* Bipolar Transistors and Related Devices (Ch. 12, Neamen)

---

## 4 Equipment

* Breadboard — 1 pc
* Digital multimeters (DMMs) — 2 pcs
* DC power supply — 1 pc
* ALD1101 and ALD1102 transistors — 1 each

---

## 5 Important Note

Before beginning the experiment, **current MUST BE LIMITED TO 100 mA** from the power supply via following procedure:

1. Disconnect everything from the output port of the power supply except the connection between the ‘+’ and GND terminals.
2. Turn the current limit to an arbitrary high value.
3. Set the output voltage to 5 V.
4. Turn the current limit to zero.
5. Connect a wire across the ‘+’ and ‘−’ terminals.
6. Slowly increase up the current limit until the ammeter reading of the power supply reaches 100mA.
7. Turn off the power supply and remove the short.
8. Repeat 1) through 7) on the other output of the power supply.
9. Turn on the power supply. Do not change the current limit.

---

## 6 Procedure

### 6.1 Quick MOSFET check with a multimeter:

MOSFET is like a capacitor between its Gate and Source terminals and between its Gate and Drain terminals. Test MOSFET using the following steps:

1. **Caution!** Don’t touch by hand only the gate terminal as it may damage the transistor.
2. Short all terminals i.e., Gate, Source and Drain of the MOSFET with your hand, making sure you touch either the source or the drain terminal first. This step discharges the capacitor in case it was already charged.
3. Measure the resistance between the Drain and Source terminals with a multimeter. It should be an open circuit for a good MOSFET.
4. Apply a V<sub>GS</sub> of a few volts (positive for NMOS and negative for PMOS) for a few seconds and then measure the Drain to Source resistance again. It must be short circuit for a working MOSFET.

---

### 6.2 Part I – Planer MOSFET IV characteristics measurement (in-lab)

To help you with the measurements, the output characteristics of the ALD1101 and ALD1102 MOSFETs have been measured with a Semiconductor Parameter Analyzer (Agilent 4155C) and are reproduced in Figure 1.

---

![Figure 1: Output characteristics of the n-channel MOSFET (ALD1101) and p-channel MOSFET (ALD1102)](image-placeholder)

**Figure 1: Output characteristics of the (a) n-channel MOSFET (ALD1101) and the (b) p-channel MOSFET (ALD1102)**

---

The test setups for the n- and p-channel MOSFETs are shown in Figure 2 (a) and (b), respectively. Figure 2 (c) shows the package pins. Please note that the ALD1101 and the ALD1102 ICs contain an n-MOS and a p-MOS pair, respectively. Each device in the pair has its own source, gate, and drain terminal, and shares a common substrate (Bulk) terminal connected to the substrates of the both the devices. For this experiment, you will need only one of the two devices of the pair.

![Figure 2: DC measurement circuit schematics](image-placeholder)

**Figure 2: DC measurement circuit schematics of (a) the n-MOSFET and (b) p-MOSFET, and (c) package pins for the n- and p-channel MOSFET pairs**

---

1. Build the test setup for the **n-MOSFET (ALD1101)** on the breadboard (See Figure 2(a)).
   Set DMM₁ for the DC voltage measurement and DMM₂ for the DC current measurement. DMM₁ is used to measure the drain-source (V<sub>DS</sub>) and gate-source (V<sub>GS</sub>) voltages. DMM₂ is connected in series to monitor the drain current (I<sub>DS</sub>).

2. Measure the transfer characteristics of the n-MOSFET by setting
   V<sub>DS</sub> to 0.04V, 1V, 4V, and 10V and measuring I<sub>D</sub> vs. V<sub>GS</sub> with 1V increments from 0V to 10V.
   Plot I<sub>D</sub> vs. V<sub>GS</sub>.
   What is the maximum drain current (I<sub>ON</sub>)?

3. Measure the output characteristics of the n-MOSFET by setting
   V<sub>GS</sub> to 0.4V, 1V, 4V, and 10V and measuring I<sub>D</sub> vs. V<sub>DS</sub> with 1V increments from 0V to 10V.
   Plot I<sub>D</sub> vs. V<sub>DS</sub>.

4. **This step may cause destructive damage to the MOSFET, so proceed only after you are satisfied with the data from steps 2) and 3).**
   Measure the breakdown region of the output characteristics by using the set-up from step 3) and by incrementing V<sub>DS</sub> beyond 10V while V<sub>GS</sub> remains fixed at 4V.
   For this measurement, V<sub>DS</sub> should be increased at smaller increments (e.g. 0.25V) in order not to burn the MOSFET.
   Increase V<sub>DS</sub> until I<sub>D</sub> is 150% of I<sub>D</sub> at V<sub>DS</sub> = 5V.

5. Repeat steps 1) through 3) for the **p-MOSFET (ALD1102)** with V<sub>DS</sub> reversed to V<sub>SD</sub> and V<sub>GS</sub> reversed to V<sub>SG</sub> (See Figure 2(b)).

---

# 6.3 Part II – Data analysis (Take home)

This part requires the use of **MATLAB** or similar software. Compare the nanoscale planer, finFET and FDSOI MOSFET technologies by analyzing the data provided. Answer the questions in your post-lab report.

---

## 6.3.1 Planar MOSFET

The measured data used in this part are included in the following files:

### **Table I planar MOSFET files**

| No. | File name                        | Device description | Channel | L<sub>drawn</sub> (nm) | W (μm) |
| --: | -------------------------------- | ------------------ | ------- | ---------------------- | ------ |
|   1 | planar_lp065_w1_n80_transfer.txt | n                  | 65      | 80×1                   |        |
|   2 | planar_lp065_w1_n80_output.txt   | n                  | 65      | 80×1                   |        |
|   3 | planar_lp090_w1_n80_transfer.txt | n                  | 90      | 80×1                   |        |
|   4 | planar_lp090_w1_n80_output.txt   | n                  | 90      | 80×1                   |        |
|   5 | planar_lp13_w1_n80_transfer.txt  | n                  | 130     | 80×1                   |        |
|   6 | planar_lp13_w1_n80_output.txt    | n                  | 130     | 80×1                   |        |
|   7 | planar_lp18_w1_n80_transfer.txt  | n                  | 180     | 80×1                   |        |
|   8 | planar_lp18_w1_n80_output.txt    | n                  | 180     | 80×1                   |        |
|   9 | planar_lp25_w1_n80_transfer.txt  | n                  | 250     | 80×1                   |        |
|  10 | planar_lp25_w1_n80_output.txt    | n                  | 250     | 80×1                   |        |
|  11 | planar_lp35_w1_n80_transfer.txt  | n                  | 350     | 80×1                   |        |
|  12 | planar_lp35_w1_n80_output.txt    | n                  | 350     | 80×1                   |        |

These measurements were performed on **n-channel MOSFETs** with different channel lengths (L) fabricated in a 65 nm technology. Along with the measurement data, these files also contain the measurement conditions. For example, the transfer characteristics files contain the V<sub>DS</sub> values at which the I<sub>DS</sub> vs. V<sub>GS</sub> sweeps were measured, and the output characteristics files contain the V<sub>GS</sub> values at which the I<sub>DS</sub> vs. V<sub>DS</sub> sweeps were measured.

Alternatively, you may use the following MATLAB file which has the data pre-imported:
**planar_lpxxx_w1_n80_data.mat**

After you have imported the data, perform the following steps:
**(MOSFET Parameter Extraction procedures are given in the appendix at the end).**

---

### 1)

Extract the threshold voltage (V<sub>t0</sub>) from the transfer characteristics in the triode region (I<sub>DS</sub> vs. V<sub>GS</sub> for V<sub>DS</sub> = 0.04V) for each of the MOSFETs with **L = 65, 90, 130, 180, 250, and 350 nm**.
Describe the observed trend for threshold voltage vs channel length.

For the **L = 65 nm** device only, plot **I<sub>DS</sub> vs. V<sub>GS</sub>** and **g<sub>m</sub> vs. V<sub>GS</sub>** at V<sub>DS</sub> = 0.04V.
Identify **V<sub>t0</sub>** on the plot. *(1 mark)*

---

### 2)

Extract the **DIBL parameter (η)** from the transfer characteristics (I<sub>DS</sub> vs. V<sub>GS</sub> at V<sub>DS</sub> = 0.04V, 1.2V) of the L = 65 nm device.
Plot **log₁₀(I<sub>DS</sub>) vs. V<sub>GS</sub>** at V<sub>DS</sub> = 0.04 and 1.2V.
Determine **η**. *(1 mark)*

---

### 3)

Extract the **channel length modulation (λ)** parameter from the output characteristics
(I<sub>DS</sub> vs. V<sub>DS</sub> for V<sub>GS</sub> = 0.2, 0.4, 0.6, 0.8, 1.0 and 1.2V)
for the n-MOSFET with **L = 65 nm**.
Why does λ change with V<sub>GS</sub>? *(1 mark)*

---

### 4)

Find **g<sub>mlin</sub>** of linear region where

[
g_{mlin} = \frac{(V'*{DS} \cdot W)}{g*{mlin(\text{peak})}} = \frac{(L_{\text{drawn}} - \Delta L)}{k'_n}
]

(See appendix).

Plot

[
\frac{(V'*{DS} \cdot W)}{g*{mlin(\text{peak})}}
\quad \text{vs} \quad
L_{\text{drawn}}
]

where L<sub>drawn</sub> is the drawn gate length for the **65 nm to 350 nm** devices.

V′<sub>DS</sub> is the drain to source voltage that has been corrected for IR losses.
Extract **k′ₙ** from the slope and **ΔL** from the x-intercept.

What is the effective gate length (**L<sub>eff</sub> = L<sub>drawn</sub> − ΔL**) of the 65 nm device? *(1 mark)*

---

## 6.3.2 FD-SOI and finFET MOSFETs

The measured IV characteristics of the n- & p-FDSOI and n- & p-finFET MOSFET devices are provided in the following files listed in the tables below.

---

### **Table II FDSOI MOSFET files**

| No. | File name                         | Channel | L<sub>drawn</sub> (nm) | W (μm)  |
| --: | --------------------------------- | ------- | ---------------------- | ------- |
|   1 | nfdsoi_lp02_wp43_n40_transfer.csv | n       | 20                     | 40×0.43 |
|   2 | nfdsoi_lp02_wp43_n40_output.csv   | n       | 20                     | 40×0.43 |
|   3 | pfdsoi_lp02_wp43_n40_transfer.csv | p       | 20                     | 40×0.43 |
|   4 | pfdsoi_lp02_wp43_n40_output.csv   | p       | 20                     | 40×0.43 |

---

### **Table III finFET MOSFET files**

| No. | File name                            | Channel | N<sub>f</sub> | N<sub>fin</sub> | L<sub>drawn</sub> | W (μm)  |
| --: | ------------------------------------ | ------- | ------------- | --------------- | ----------------- | ------- |
|   5 | nfinfet_lp008_wp09_n192_transfer.csv | n       | 48            | 4               | 8 nm              | 48×4×90 |
|   6 | nfinfet_lp008_wp09_n192_output.csv   | n       | 48            | 4               | 8 nm              | 48×4×90 |
|   7 | pfinfet_lp008_wp09_n192_transfer.csv | p       | 48            | 4               | 8 nm              | 48×4×90 |
|   8 | pfinfet_lp008_wp09_n192_output.csv   | p       | 48            | 4               | 8 nm              | 48×4×90 |

---

Like with the planar MOSFET data of the previous section, the transfer characteristics files contain the V<sub>DS</sub> values at which the I<sub>DS</sub> vs V<sub>GS</sub> sweeps were measured, and the output characteristics files contain the V<sub>GS</sub> values at which the I<sub>DS</sub> vs. V<sub>DS</sub> sweeps were measured.

After you have imported the data, follow similar steps to that performed on the planar n-MOSFET in the previous section to compare the three different technologies.

Use the **L = 65 nm n-MOSFET** analyzed previously for your comparisons to the FDSOI MOSFET (n-channel: L<sub>drawn</sub> = 20 nm, W = 80×0.43 μm) and the finFET (n-channel: L<sub>drawn</sub> = 8 nm, W = 48×4× 90 nm).

---

### 1)

Plot **I<sub>DS</sub> vs V<sub>GS</sub>** and **g<sub>m</sub> vs V<sub>GS</sub>** at the smallest V<sub>DS</sub> bias indicated and identify **V<sub>t0</sub>** on the plot (See appendix).
Plot together to enable comparisons.

---

### 2)

a) Compare the **threshold voltages** between FDSOI and finFET technologies. Note that the V<sub>GS</sub> values for which measurements are provided are the safe DC voltage operating range without risking damage. *(1 mark)*

b) Compare the **peak transconductance (g<sub>m</sub>/W)** and **on-current (I<sub>ON</sub>/W)** values between FDSOI and finFET technologies at their respective largest V<sub>DS</sub> bias for which data is provided.
*(1 mark)*

c) Compare the **subthreshold slope** of the minimum gate length n-MOSFETs in each technology. *(1 mark)*

d) Compare the **DIBL parameter** between technologies. *(1 mark)*

---

### 3)

Plot the output characteristics for the FDSOI and finFET n- and p-channel devices and extract the **channel length modulation parameter (λ)** for each. *(1 mark)*

---

### 4)

The measured HF C–V characteristics of n-FDOIS and n-finFET are shown in **Figure 3** and **Figure 4**, respectively.
Using the provided data, answer the following questions.

---

#### a)

Identify the range of V<sub>G</sub> values for which the MOSFET is in inversion or depletion. *(1 mark)*

#### b)

What are the maximum and minimum capacitance values? *(1 mark)*

#### c)

If the measured FDSOI MOSFET in **Figure 3** is composed of **40 gate fingers in parallel**, each with length **L<sub>g</sub> = 20 nm** and width **W<sub>f</sub> = 430 nm**, then estimate the equivalent oxide thickness **t<sub>OXE</sub>** of the n-FDSOI MOSFET. *(1 mark)*

#### d)

If the measured n-finFET in **Figure 4** is composed of **192 fins in parallel**, each with length **L<sub>g</sub> = 8 nm** and effective width **W<sub>f</sub> = 90 nm**, estimate the equivalent oxide thickness **t<sub>OXE</sub>** of the n-finFET and the thickness of the silicon fin. *(1 mark)*

---

![Figure 3](image-placeholder)
**Figure 3** The measured HF C-V characteristics of a FDSOI n-MOSFET varactor with 40 devices in parallel, gate length L<sub>g</sub> = 20 nm and finger width W<sub>f</sub> = 430 nm.

![Figure 4](image-placeholder)
**Figure 4** Measured HF C-V characteristics of a n-FinFET with 192 fins, gate length L<sub>g</sub> = 8 nm and effective fin width W<sub>f</sub> = 90 nm.

---

# 6.3.3 Commercial BiCMOS Technologies

You are provided with the following **20log₁₀|H₂₁| vs. frequency** measurements of npn SiGe HBTs in three commercial SiGe BiCMOS technologies:

* bicmos6g_H21_vs_freq.txt
* bicmos9_H21_vs_freq.txt
* b9mw_H21_vs_freq.txt

Please note that the data contained in these files have been de-embedded.

---

### 1)

Plot **20log₁₀|H₂₁| vs. frequency** on a semi-log scale.
From the −20 dB/decade region of the plot, extract the **f<sub>T</sub>** for all devices and at each bias point. *(1 mark)*

### 2)

On the same figure, plot the **f<sub>T</sub> vs. I<sub>C</sub>** characteristics for each device on a semi-log scale.
For each technology provide the **peak f<sub>T</sub>** frequency and the current density at which it occurs. *(1 mark)*

---

# 7 Pre-Lab Questions

1. What is the meaning of the threshold voltage (V<sub>t</sub>)?
   Explain a procedure to measure the threshold voltage. *(1 mark)*

2. MOSFETs are four-terminal devices. For each n-channel and p-channel device, explain how the body (substrate) terminal should be connected.
   What could happen if the substrate voltage is not appropriately biased? *(1 mark)*

3. What is the DIBL and channel length modulation and how to measure them?
   Comparing between measured planar MOSFETs and nanoscale planar MOSFET (data provided) which would show higher impact of DIBL and channel length modulation? *(1 mark)*

---

# 8 Results

For the measured **n- and p-channel MOSFETs**, include the following data in your post-lab report:

* Plot **I<sub>D</sub> vs. V<sub>GS</sub>** at V<sub>DS</sub> = 10V with I<sub>ON</sub> labeled *(1 mark)*
* Plot **g<sub>m</sub> vs. V<sub>GS</sub>** (g<sub>m</sub> = ΔI<sub>D</sub>/ΔV<sub>GS</sub>) at V<sub>DS</sub> = 10V with g<sub>m(peak)</sub> labeled *(1 mark)*
* Compute the threshold voltage (V<sub>t0</sub>) *(1 mark)*
* Plot **I<sub>D</sub> vs. V<sub>DS</sub>** and identify the breakdown region *(1 mark)*
* Plot **g<sub>d</sub> vs. V<sub>DS</sub>** (g<sub>d</sub> = ΔI<sub>D</sub>/ΔV<sub>DS</sub>) and extract λ *(1 mark)*

For the data analysis, include all the answers to the questions in your post-lab report.

---

# 9 Post-Lab Questions

Post lab report should include all the results from Part 1 and 2 data analysis as described in the previous sections.

---

# 10 Appendix : Parameter Extraction

---

## **Threshold voltage (Vₜ₀)**

![Threshold voltage figure](image-placeholder)

* Use the linear region of the transfer characteristics (I<sub>DS</sub> vs. V<sub>GS</sub>) when V<sub>DS</sub> is close to zero (i.e. V<sub>DS</sub> = 0.04V)
* Plot g<sub>m</sub> vs. V<sub>GS</sub>.
  Remember

  [
  g_m = \frac{\partial I_D}{\partial V_{GS}}
  ]

  so obtain g<sub>m</sub> from the plot of I<sub>D</sub> vs. V<sub>GS</sub>.
* From the region where g<sub>m</sub> peaks draw line on the I–V characteristics
* Find the x-axis intercept of this line

  [
  V_{t0} = \text{x-axis intercept} - \frac{3kT}{q}
  ]

---

## **DIBL (η)**

![DIBL figure](image-placeholder)

* From the sub-threshold region (**log₁₀ I<sub>D</sub> vs. V<sub>GS</sub>** plot), several V<sub>T</sub>’s below the threshold voltage, read the difference in V<sub>GS</sub> at fixed current between the V<sub>DS</sub> = 0.04 V and V<sub>DS</sub> = 1.2 V curves.

* The DIBL parameter (η) is found with

  [
  \eta = \Delta V_{GS} / \Delta V_{DS}
  ]

* Now, the DIBL parameter can be used to find the threshold voltage as a function of V<sub>DS</sub> with

  [
  V_t = V_{t0} - \eta V_{DS}
  ]

---

# Channel length modulation (λ)

![Channel length modulation figure](image-placeholder)

* In the output characteristics (I<sub>DS</sub> vs. V<sub>DS</sub>), draw a line in the saturation region for each curve corresponding to a constant V<sub>GS</sub>.
* The x-axis intercept of this line is **V<sub>A</sub>**
* The channel modulation parameter is found with

  [
  \lambda = 1 / V_A
  ]

---

# Effective Channel Length (Lₑff)

![gm peak figure](image-placeholder)

* Use the linear region of the transfer characteristics (I<sub>DS</sub> vs. V<sub>GS</sub>) when V<sub>DS</sub> is close to zero (i.e. V<sub>DS</sub> = 0.04V)

* Plot g<sub>m</sub> vs. V<sub>GS</sub> and find the peak g<sub>m</sub> (g<sub>m(peak)</sub>) and the current at which it occurs (I<sub>DS(peak gm)</sub>)

* Find the IR* voltage loss and correct the V<sub>DS</sub> with

  [
  V'*{DS} = V*{DS} - I_{DS(\text{peak gm})}(R_S + R_D)
  ]

* In a 65nm technology, assume R’<sub>D</sub> and R’<sub>S</sub> = 220 Ω·µm, to find R<sub>S</sub>, R<sub>D</sub> divide by the transistor width:
  [
  R_D = R'_D / W,\quad R_S = R'_S / W
  ]

---

### Linear region formula

[
g_{mlin} = \frac{\partial I_{DS}}{\partial V_{GS}}
= \left[\frac{\partial}{\partial V_{GS}}
\left( k_n C_{ox} \frac{W}{L_{drawn} - \Delta L}
(V_{GS} - V_t - \frac{V'*{DS}}{2})V'*{DS}
\right)\right]
]

[
\Rightarrow \frac{V'*{DS} W}{g*{mlin(\text{peak})}}
= \frac{L_{drawn} - \Delta L}{k_n}
]

* Plot

  [
  \frac{V'*{DS} W}{g*{mlin(\text{peak})}}
  \quad \text{vs.} \quad
  L_{drawn}
  ]

  for measurement data with different channel lengths all in the same technology.
  *This method works since the delta between L<sub>drawn</sub> values is defined lithographically (ΔL is constant)*

* Find **kₙ** from **1/slope** and **ΔL** from the **x-axis intercept**

---

* Calculate the effective channel length with

  [
  L_{eff} = L_{drawn} - \Delta L
  ]

---

# Others

* Use the oxide thickness, t<sub>OX</sub> to find

  [
  C_{OX} = \varepsilon_0 \varepsilon_{OX} / t_{OX}
  ]

  where ε<sub>OX</sub> = 4 for SiO₂

* Electron mobility (μₙ) can be found using

  [
  k_n = \mu_n C_{OX}
  ]

---

# Extracting fₜ from S-parameter Measurements

![H21 figure](image-placeholder)

* Transform S<sub>DUT</sub> into H-parameters by using the **s2h() MATLAB function**
* Use **H<sub>DUT</sub>(2,1)**, which represents the current gain, to plot **20log₁₀(H(2,1)) vs. frequency** on semi-log scale
* Draw a line in the −20 dB/decade region
* The x-axis intercept is **f<sub>T</sub>**

---

# Cautionary Note About De-embedding Devices Mounted on a PCB

![Artifact figure](image-placeholder)

* There are physical variations between each PCB; these variations are larger on the PCB than on-chip
* As a result, an artifact may appear in the H(2,1) plot at higher frequencies.
* This artifact comes from:

  * physical difference between the fixtures that are measured and the fixture characteristics that are used to de-embed
  * distributed effects of the device package and leads
* As a result, use H₂₁ portion below ~1.5GHz to find **f<sub>T</sub>**

---

# fₜ vs. I꜀ Characteristics

![fT vs Ic figure](image-placeholder)

* Extracting **f<sub>T</sub>** at different currents and plot it similar to the one shown beside.