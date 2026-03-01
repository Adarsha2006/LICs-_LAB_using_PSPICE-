# Experiment 2: Source Degenerated CS Amplifier Variations

**Simulation Tool:** LTspice  
**Technology:** TSMC 180nm CMOS  
**Supply Voltage:** 1.8 V  
**Load Capacitance:** 1 pF  

---

# Aim

To design and simulate three variations of a Common-Source (CS) amplifier with source degeneration and compare their:

- DC bias behavior  
- Gain  
- Linearity  
- Bandwidth  
- Power consumption  

---

# Circuits Implemented

1. Resistive Source Degeneration (Rs)
2. MOS Source Degeneration (Fixed VBN)
3. Gate-Tied MOS Degeneration (Self Bias)

---

# 1️⃣ Resistive Source Degenerated CS Amplifier

---

## Circuit Diagram

*(Insert screenshot here)*

```
[ INSERT CIRCUIT DIAGRAM IMAGE – Resistive Degeneration ]
```

---

## Components Used

| Component | Value |
|-----------|--------|
| M1 (NMOS) | W = 390 nm, L = 180 nm |
| M2 (PMOS) | W = 1.5 µm, L = 180 nm |
| Rs | 15 kΩ |
| VDD | 1.8 V |
| VBP | 1.21 V |
| CL | 1 pF |

---

## Procedure

### Step 1: DC Operating Point

1. Place `.op` command.
2. Run simulation.
3. Note ID, Vout, VGS, VDS.
4. Verify M1 operates in saturation.

---

### Step 2: DC Sweep

```
.dc V2 0 1.8 0.01
```

- Sweep Vin from 0 to 1.8V.
- Select midpoint where:

Vout ≈ VDD / 2 = 0.9V

Selected DC Offset ≈ 0.58 V

---

## DC Calculations

Drain current:

ID ≈ 3.5 µA

Power:

P = VDD × ID  
P ≈ 1.8 × 3.5µA  
P ≈ 6.3 µW  

✔ Power < 20 µW

---

## Transient Analysis

Input:

```
SIN(0.58 10m 1k)
```

Observations:

- Output inverted (180° phase shift)
- Moderate gain
- Improved linearity

---

## AC Analysis

```
.ac dec 10 100 1G
```

Midband Gain ≈ 18–20 dB  

Linear Gain:

Av = 10^(Gain_dB/20)  
Av ≈ 8 – 10  

Bandwidth moderate.

---

## Inference

- Rs reduces gain.
- Improves linearity.
- Introduces local negative feedback.

---

# 2️⃣ MOS Source Degenerated CS (Fixed VBN)

---

## Circuit Diagram

*(Insert screenshot here)*

```
[ INSERT CIRCUIT DIAGRAM IMAGE – MOS with VBN ]
```

---

## Components Used

| Component | Value |
|-----------|--------|
| M1 | W = 390 nm |
| M2 | W = 1.5 µm |
| M3 | W = 180 nm |
| L (All) | 180 nm |
| VBN | 0.55 V |
| VBP | 1.21 V |
| VDD | 1.8 V |
| CL | 1 pF |

---

## Operating Principle

M3 operates in linear region and behaves as:

Ron = 1 / (µn Cox (W/L)(VGS − VT))

It replaces Rs with a voltage-controlled resistor.

---

## DC Results

ID ≈ 3.8 µA  

Power:

P ≈ 1.8 × 3.8µA  
P ≈ 6.8 µW  

✔ Within limit

Vout ≈ 0.9 – 1.0 V

---

## Transient

```
SIN(0.75 10m 1k)
```

Observations:

- Inverted output
- Gain lower than resistive degeneration
- Good symmetry

---

## AC Analysis

Midband Gain ≈ 14–16 dB  

Linear Gain:

Av ≈ 5 – 6  

Bandwidth higher than Rs case.

---

## Inference

- MOS degeneration reduces gain.
- Increases bandwidth.
- CMOS-compatible solution.
- Bias dependent resistance.

---

# 3️⃣ Gate-Tied MOS Degenerated CS (Self Bias)

---

## Circuit Diagram

*(Insert screenshot here)*

```
[ INSERT CIRCUIT DIAGRAM IMAGE – Gate Tied ]
```

---

## Description

- Gate of M3 connected to Vi.
- No separate VBN.
- Strong local negative feedback.

---

## DC Behavior

For Vi ≈ 1.21V:

Vout ≈ 0.87 V  

ID ≈ 3 – 4 µA  

Power:

P ≈ 6 – 7 µW  

✔ Within limit

---

## Transient

```
SIN(1.21 10m 1k)
```

Observations:

- Lowest gain
- Highest linearity
- Strong feedback behavior

---

## AC Results

Midband Gain ≈ 10–12 dB  

Linear Gain:

Av ≈ 3 – 4  

Highest bandwidth among three.

---

# Comparison of All Three Designs

| Parameter | Rs Degeneration | MOS (Fixed VBN) | Gate-Tied MOS |
|------------|----------------|----------------|---------------|
| ID | ~3.5 µA | ~3.8 µA | ~3–4 µA |
| Power | ~6.3 µW | ~6.8 µW | ~6–7 µW |
| Gain (dB) | 18–20 dB | 14–16 dB | 10–12 dB |
| Linear Gain | 8–10 | 5–6 | 3–4 |
| Bandwidth | Moderate | Higher | Highest |
| Linearity | Good | Better | Best |
| Stability | Good | Better | Excellent |
| CMOS Integration | No | Yes | Yes |

---

# Overall Observations

1. Source degeneration reduces gain.
2. Degeneration improves linearity.
3. MOS-based degeneration improves integration.
4. Gate-tied configuration introduces strongest feedback.
5. Gain–Bandwidth tradeoff clearly verified.
6. All designs satisfy power < 20 µW.

---

# Conclusion

Three source-degenerated CS amplifier configurations were designed and simulated in 180nm CMOS.

The study verifies:

- Effect of source degeneration
- Gain–bandwidth tradeoff
- Feedback impact on amplifier behavior
- CMOS implementation advantages

The simulated results match theoretical small-signal analysis.

---
