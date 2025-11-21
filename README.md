<img width="1795" height="3024" alt="image" src="https://github.com/user-attachments/assets/d5de6857-3b2e-4935-ac9f-a59d60702748" /><img width="1795" height="3024" alt="image" src="https://github.com/user-attachments/assets/54d3ba85-a138-466e-a21e-2561f8c2aa8d" /># Digital Tachometer Design using Verilog HDL

This repository contains the hardware description language (Verilog HDL) implementation and formal documentation for a **Digital Tachometer** system. The design measures the rotational speed (RPM) of a simulated motor using the **Fixed Gate Time Method**, chosen for its simplicity and high accuracy in digital hardware implementations.

---

## 📘 Project Overview

The objective of this project is to design a **synthesizable, robust, real-time digital speed measurement circuit**. The tachometer uses a **modular and synchronous architecture**, where each major function is separated into clean Verilog modules:

- Pulse Generation (motor simulation)
- Gate Timing
- Pulse Counting & RPM Calculation

<img width="1795" height="3024" alt="- visual selection" src="https://github.com/user-attachments/assets/e1dd9664-262e-4f13-9394-78e712ccc54e" />


### ✔ Measurement Method

- Fixed Gate Time:  
  [ T_gate = 0.1 seconds ]
- Implemented using a large counter clocked by a 50 MHz system clock.

### ✔ Timing Parameters

- Clock frequency: 50 MHz  
- Gate window cycles:  
  [ 50,000,000 × 0.1 = 5,000,000 cycles ]

### ✔ RPM Formula

[ RPM = ( N_pulses / (PPR × T_gate) ) × 60 ]

---

## 📂 Repository Contents

| File | Description |
|------|-------------|
| **digital_tachometer_code.v** | Contains all Verilog modules: Motor_Pulse_Generator, RPM_Counter, and the tb_Tachometer testbench. |
| **REPORT.md** | Full technical documentation including methodology, timing calculations, synthesis critique, and verification. |
| **README.md** | This project overview file. |
| **.gitignore** | Excludes simulation and synthesis-generated temporary files. |

---

## 🔧 Module Breakdown

### **1. Motor_Pulse_Generator**
A clock-divider module that simulates encoder pulses of a rotating motor. It is parameterized to generate pulses equivalent to 600 RPM for verification.

### **2. RPM_Counter**
The main measurement block containing:
- Gate timer for the 0.1 s measurement interval  
- Pulse counter that counts motor pulses during the gate time

### **3. tb_Tachometer (Testbench)**
The verification environment:
- Generates clock and reset  
- Starts simulated motor  
- After measurement, performs the RPM calculation  
- Prints results for verification

---

## 🧪 Quick Verification (600 RPM)

Using:
- 100 PPR encoder  
- 0.1 s gate time  
- 600 RPM expected speed  

Expected pulse count:

[ N_pulses = (600 × 100 × 0.1) / 60 = 100 ]

Simulation output:



<img width="1576" height="817" alt="image" src="https://github.com/user-attachments/assets/ef47baa4-a625-43c2-b0c3-54f3f6924da3" />
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/5099e444-cfd6-4456-8ff7-74e58e205d89" />

This will execute the testbench and display the calculation results in the console.
