# MDOF-Vibrations

# Detailed Comments and Theory on the Vibration Analysis Codes

## Theory Behind the Code

This code analyzes the vibrations of a two-degree-of-freedom (2-DOF) system using numerical methods. The system is modeled with mass and stiffness matrices, and its dynamic behavior is analyzed under free and forced vibration scenarios. Key results include natural frequencies, mode shapes, time-domain responses, phase portraits, and frequency responses.

---

### System Parameters and Equations

#### Mass and Stiffness Matrices:
- **Mass Matrix (M):**
  \[
  M = \begin{bmatrix}
  m_1 & 0 \\
  0 & m_2
  \end{bmatrix}
  \]

- **Stiffness Matrix (K):**
  \[
  K = \begin{bmatrix}
  k_1 + k_2 & -k_2 \\
  -k_2 & k_2 + k_3
  \end{bmatrix}
  \]

#### Eigenvalue Problem:
The natural frequencies (\( \omega_n \)) and mode shapes are obtained by solving:
\[
\text{Eigenvalue Problem: } \text{inv}(M)K\phi = \lambda\phi
\]
\[
\text{Natural Frequencies: } \omega_n = \sqrt{\lambda}
\]

---

### Time Response Simulation (Free Vibration)

#### Dynamic Equations:
- State-space representation:
  \[
  \dot{z} = \begin{bmatrix}
  v \\
  a
  \end{bmatrix}
  \]
- Acceleration:
  \[
  a = -M^{-1}Kx
  \]

#### Initial Conditions:
- Displacements: \( x_1(0) = 1.0, x_2(0) = 0.5 \)
- Velocities: \( v_1(0) = 0, v_2(0) = 0 \)

---

### Phase Portrait for Each Degree of Freedom
- Plots displacement vs. velocity for each DOF:
  - DOF 1: \( (x_1, v_1) \)
  - DOF 2: \( (x_2, v_2) \)

---

### Frequency Response via FFT
- **FFT of Displacement:**
  - Identify dominant frequencies from the time-domain response.
  - Frequency bins: \( \text{fft}(x_1) \)

---

### Forced Vibration Analysis

#### Damping Matrix:
- Assumes proportional damping:
  \[
  D = \alpha M + \beta K
  \]
  where \( \alpha \) and \( \beta \) are damping coefficients.

#### Dynamic Equation for Forced Vibration:
- Equation of motion:
  \[
  M\ddot{x} + D\dot{x} + Kx = F(t)
  \]
- Force applied:
  \[
  F(t) = F\cos(\omega_\text{force}t)
  \]

#### Steady-State Amplitude:
- Steady-state amplitude of displacement:
  \[
  X = \frac{F}{\sqrt{(k - m\omega^2)^2 + (c\omega)^2}}
  \]

---

## Summary of Key Results
- **Natural Frequencies:** Computed using eigenvalues.
- **Mode Shapes:** Normalized eigenvectors.
- **Time-Domain Response:** Solved using numerical integration of dynamic equations.
- **Phase Portraits:** Visualize dynamics in the state space.
- **Frequency Response:** Steady-state amplitude vs. forcing frequency.
