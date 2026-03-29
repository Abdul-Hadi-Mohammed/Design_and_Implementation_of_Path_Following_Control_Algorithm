# Design and Implementation of a Path Following Control Algorithm

This project, developed for the **Introduction to Autonomous Driving (KFT16480)** course at **Westsächsische Hochschule Zwickau**, focuses on the design and implementation of a robust vehicle path-following system using MATLAB and Simulink.

---

## 🚀 Overview
The system enables a vehicle to autonomously execute a predefined trajectory with millimeter precision. It bridges the gap between path planning and motion by utilizing two primary control pillars:

* **Lateral Control (Steering):** Controlling the front wheel angle to minimize path deviation.
* **Longitudinal Control (Speed):** Managing throttle and braking to maintain the target velocity profile.

---

## 🛠️ Control Strategies

### Lateral Control: Stanley Controller
The **Stanley Controller** was selected for lateral control due to its geometric robustness, explicit handling of errors, and low computational cost. It computes the steering angle based on:

1.  **Heading Error ($\psi_e$):** The difference between the vehicle's yaw angle and the reference path direction.
2.  **Cross-Track Error ($e$):** The lateral distance between the front axle and the nearest path point.

**Control Law:**
$$\delta_{v}=\psi_{e}+arctan\left(\frac{k \cdot e}{v+v_{comp}}\right)$$

### Longitudinal Control: PID Controller
A **PID controller** manages vehicle acceleration due to its simplicity and wide application in automotive longitudinal control.
* **Input:** Speed error (difference between desired and actual speed).
* **Output:** Longitudinal acceleration command.

---

## 📈 Optimization & Tuning
The controller parameters were refined through a combination of automated optimization (SQP) and manual tuning to find the optimal balance between lateral and longitudinal precision.

### Final Controller Parameters (Best Sample)
| Parameter | Value |
| :--- | :--- |
| Stanley Gain ($K$) | 1.5 |
| Softening Gain ($K_s$) | 1.5 |
| Wheelbase ($L$) | 3 |
| $P$ (Proportional) | 3 |
| $I$ (Integral) | 0.5 |
| $D$ (Derivative) | 0.1 |

*Note: Data based on **Sample 13**, which achieved the lowest total error during testing.*

---

## 🏁 Results
Simulation results confirm that the architecture provides stable and accurate performance.

* **Path Precision:** The vehicle effectively minimized cross-track error, maintaining the reference trajectory even through complex curves.
* **Velocity Tracking:** The PID controller successfully adjusted the actual velocity to match the reference profile despite dynamic changes.

---

## 👥 Contributors (Group 4)
* Syed Siddiq Shakir (57975)
* Abdul Hadi Mohammed (57882)
* Abdul Sammad (53761)

**Instructor:** Prof. Dr.-Ing. Rick Voßwinkel

---

## 📚 References
* Hoffmann, G. M., et al. (2007). *Autonomous Automobile Trajectory Tracking for Off-Road Driving*.
* Messner, W., et al. (2023). *Control Tutorials for MATLAB and Simulink - PID Control*.
* MathWorks Student Competitions Team (2021). *Vehicle Path Tracking Using Stanley Controller*.
