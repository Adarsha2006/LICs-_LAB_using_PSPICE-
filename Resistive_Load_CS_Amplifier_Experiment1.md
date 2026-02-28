<img width="1916" height="850" alt="image" src="https://github.com/user-attachments/assets/640fa847-8ce2-4d40-85ef-a81bf043f293" /># Experiment 1: Resistive Load CS Amplifier

**Simulation Tool:** LTspice  
**Technology:** TSMC 180nm CMOS 

---

## Aim

To design and simulate a Resistive Load Common Source (CS) Amplifier using 180nm CMOS technology.

## Components Used

| Component | Value / Model |
|-----------|--------------|
| NMOS | W = 540nm , L = 180nm |
| R | 20kΩ, 75kΩ, 90kΩ, 130kΩ |
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
# A)Circuit Diagram
<img width="1268" height="821" alt="image" src="https://github.com/user-attachments/assets/34596f12-c655-4017-8b0b-778fea5716c7" />



# B) DC Analysis

### Objective:
To determine operating region and select optimal bias point.


#### a) DC Operating Point


<img width="846" height="635" alt="DC OP PNT" src="https://github.com/user-attachments/assets/93cc18c4-8835-47e7-9720-1286c376e282" />


#### b) DC Sweep


<img width="1918" height="850" alt="dcsweep90k" src="https://github.com/user-attachments/assets/c2b135ba-ed13-469d-a492-07361e70dc23" />



### Observations:

- Increasing R increases voltage gain.
- Steepest transfer characteristic observed for R = 130kΩ.
- Midpoint condition:

    Vout = VDD / 2 = 0.9 V

- Corresponding input bias voltage:

    Vin = 0.549 V

  # Effect of Varying R

- Increasing R increases gain.
- Increasing R reduces bandwidth.
- Demonstrates gain–bandwidth tradeoff.

<img width="1918" height="850" alt="dcsweepvarR" src="https://github.com/user-attachments/assets/19981c97-ca8f-4314-8324-f06d2bae609b" />



# Effect of Varying W

- Increasing W increases drain current.
- gm increases.
- Gain increases.
- Q-point shifts left in transfer curve.

<img width="1918" height="847" alt="dcsweepvarW" src="https://github.com/user-attachments/assets/da82d59c-a5eb-44d5-93bb-1497dde596a0" />


### Inference:

- MOSFET operates in saturation region at selected Q-point.



# C) Transient Analysis

### Input Applied:

SIN(0.549 10m 1k)

- DC offset = 0.549 V
- Amplitude = 10 mV
- Frequency = 1 kHz

### Observations:

- Output waveform is inverted (180° phase shift).
- Output DC level ≈ 0.9 V.


<img width="1918" height="847" alt="transient analysis" src="https://github.com/user-attachments/assets/629a7607-7053-4e9e-a9d5-981fe7ba9a09" />




### Inference:

- CS amplifier shows proper amplification.
- Amplifier operates in active region.



# D) AC Analysis

### AC Command Used:

.ac dec 100 1 1G

### Observations:

- High-frequency cutoff ≈ 1 MHz
- Phase shift confirms inverting behavior.


<img width="1916" height="850" alt="image" src="https://github.com/user-attachments/assets/1c06dc4f-a527-41ee-b125-6a9f7de44b35" />



---

# Overall Inferences

1. Proper biasing is essential for symmetrical output swing.
2. Gain is directly proportional to R.
3. Bandwidth is inversely proportional to R.
4. Output capacitor introduces dominant pole.
5. CS amplifier exhibits 180° phase inversion.
6. Gain–bandwidth tradeoff observed experimentally.

---

# Conclusion

The Resistive Load CS Amplifier was successfully designed and simulated using 180nm CMOS technology in LTspice. The effect of varying load resistance (RD), transistor width (W), and bias voltage was studied through DC, Transient, and AC analysis. The experiment clearly verifies the gain–bandwidth tradeoff and the inverting nature of the Common Source amplifier.

---


