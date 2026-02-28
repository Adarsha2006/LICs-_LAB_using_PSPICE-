# Experiment 1: Resistive Load CS Amplifier

**Simulation Tool:** LTspice  
**Technology:** TSMC 180nm CMOS 

---

## Aim

To design and simulate a Resistive Load Common Source (CS) Amplifier using 180nm CMOS technology.

## Components Used

| Component | Value / Model |
|-----------|--------------|
| NMOS | W = 540nm , L = 180nm |
| R | 20kΩ, 75kΩ, 130kΩ |
| Supply Voltage | 1.8 V |
| Load Capacitor | 1 pF |
| Input Source | Sinusoidal |
| DC Offset | 0.549 V |
| AC Amplitude | 1 V (for AC analysis) |

---

## Design Details

- Channel Length (L) fixed at 180nm (technology minimum)
- Channel Width (W) initially 540nm (W/L = 3)
- Load capacitor of 1pF connected at output node
- RD varied to study gain variation
- Q-point selected using DC sweep

---

# A) DC Analysis

### Objective:
To determine operating region and select optimal bias point.

### Observations:

- Increasing RD increases voltage gain.
- Steepest transfer characteristic observed for RD = 130kΩ.
- Midpoint condition:

    Vout = VDD / 2 = 0.9 V

- Corresponding input bias voltage:

    Vin = 0.549 V

### Inference:

- MOSFET operates in saturation region at selected Q-point.
- Proper biasing ensures maximum symmetrical output swing.

---

# B) Transient Analysis

### Input Applied:

SIN(0.549 10m 1k)

- DC offset = 0.549 V
- Amplitude = 10 mV
- Frequency = 1 kHz

### Observations:

- Output waveform is inverted (180° phase shift).
- Output DC level ≈ 0.9 V.
- No clipping observed.
- Voltage gain ≈ 30 V/V (approx).

### Inference:

- CS amplifier shows proper amplification.
- Bias point ensures symmetrical signal swing.
- Amplifier operates in active region.

---

# C) AC Analysis

### AC Command Used:

.ac dec 100 1 1G

### Observations:

- Midband Gain ≈ 30 dB
- Linear Gain ≈ 31.6 V/V
- High-frequency cutoff ≈ 1 MHz
- Phase shift confirms inverting behavior.

### Bandwidth Calculation:

Since RD = 130kΩ and CL = 1pF:

fH = 1 / (2π R C)

fH ≈ 1 / (2π × 130k × 1pF)

fH ≈ 1.2 MHz

This matches simulation results.

---

# Effect of Varying RD

- Increasing RD increases gain.
- Increasing RD reduces bandwidth.
- Demonstrates gain–bandwidth tradeoff.

---

# Effect of Varying W

- Increasing W increases drain current.
- gm increases.
- Gain increases.
- Q-point shifts left in transfer curve.

---

# Overall Inferences

1. Proper biasing is essential for symmetrical output swing.
2. Gain is directly proportional to RD.
3. Bandwidth is inversely proportional to RD.
4. Output capacitor introduces dominant pole.
5. CS amplifier exhibits 180° phase inversion.
6. Gain–bandwidth tradeoff observed experimentally.

---

# Conclusion

The Resistive Load CS Amplifier was successfully designed and simulated using 180nm CMOS technology in LTspice. The effect of varying load resistance (RD), transistor width (W), and bias voltage was studied through DC, Transient, and AC analysis. The amplifier demonstrated a midband gain of approximately 30 dB and a bandwidth of approximately 1 MHz. The experiment clearly verifies the gain–bandwidth tradeoff and the inverting nature of the Common Source amplifier.

---

**Verified By:**  
Dr. Yajunath Kaliyath  
Assistant Professor, ECED, NIE Mysore
