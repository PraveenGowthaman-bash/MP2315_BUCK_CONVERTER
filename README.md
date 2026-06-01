# MP2315 Synchronous Buck Converter – 12V to 5V @ 3A

---

## 🎯 What is this?
A modern, SMD buck converter that replaces outdated LM2596 modules. Designed to be embedded on a PCB, not plugged as a through-hole module.

**Input:** 12V  
**Output:** 5V @ 3A  
**Switching Frequency:** 500kHz  
**Efficiency:** ~92%  
**Output Ripple:** <1mV  

---

## 🧠 Why Each Component?

| Component | Choice | Why |
|-----------|--------|-----|
| **MP2315** | Synchronous buck IC | No external diode, higher efficiency, 3A capability, ₹65 on KTron |
| **Inductor (10µH, SRP7050TA-100M)** | 10µH, 4A, 60mΩ DCR | Lower ripple than 5.5µH, 7.5A Isat gives 2.3x margin, DCR acceptable (0.54W loss → 47°C) |
| **Input caps** | 22µF + 0.1µF ceramic | Bulk + high-frequency decoupling. 25V rating for safety |
| **Output caps** | 22µF + 0.1µF ceramic | Ripple = 0.66mV (clean enough for ESP32 ADC) |
| **Feedback network (R1,R2,Rt)** | 40.2k, 7.5k, 20k | T-type network per datasheet Table 1. Sets output to 5.09V |
| **Cboot** | 100nF | Standard bootstrap cap for high-side gate drive |

---

## 📊 Key Calculations

| Parameter | Formula | Value |
|-----------|---------|-------|
| Duty cycle | VOUT/VIN | 41.7% |
| Inductor ripple (ΔIL) | VOUT×(1-D)/(fS×L) | 0.58A |
| Peak current | ILOAD + ΔIL/2 | 3.29A (7.5A Isat → safe) |
| Output ripple | VOUT×(1-D)/(8×fS²×L×COUT) | 0.66mV |
| Inductor loss | ILOAD² × DCR | 0.54W (22°C rise) |

All values within limits. 30% ripple rule satisfied. Peak current has 2.3x margin.

---

## 🖥️ PCB Layout Notes

- Power loop (CIN → IC → L1 → COUT → GND) kept tight  
- FB trace thin, routed AFTER output cap, away from inductor  
- Thermal vias (4–6, 15mil) under IC exposed pad  
- 45° copper corners, traces from pad centers  

---

## 📁 Files in this Repo

| File | What it is |
|------|-------------|
| `.PrjPcb` | Altium project |
| `.SchDoc` | Schematic |
| `.PcbDoc` | PCB layout |
| `.pdf` | Schematic & layout (printable) |
| `.png` | 3D renders (front/back) |

---

## 🚀 Status

✅ Schematic & layout done  
⏳ PCB order pending  
⏳ Assembly & test pending  

---

## 👤 Author

Praveen Gowthaman – Hardware Design Intern

