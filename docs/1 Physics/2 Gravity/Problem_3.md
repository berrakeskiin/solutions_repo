# 🛰️ Problem 3: Trajectories of a Freely Released Payload Near Earth

## 🎯 Motivation

When an object is released from a moving rocket near Earth, its trajectory depends on initial conditions and gravitational forces. This scenario blends principles of orbital mechanics and numerical methods. Understanding these paths is essential for mission planning, satellite deployment, or reentry calculations.

---

## 🌌 Theoretical Background

The possible types of trajectories are:

- **Elliptical**: Bound orbit, velocity less than escape velocity
- **Parabolic**: Borderline escape, velocity equals escape velocity
- **Hyperbolic**: Escape trajectory, velocity greater than escape velocity

The nature of the trajectory depends on the **total mechanical energy**:

$$
E = K + U = \frac{1}{2}mv^2 - \frac{GMm}{r}
$$

- If
 $$
E < 0
 $$
: Elliptical orbit  
- If 
$$
    E = 0 
    $$
    : Parabolic escape  
- If
 $$
  E > 0
   $$
   : Hyperbolic escape

---

## 🧠 Numerical Simulation

We model the payload's path using Newton's law of gravitation:

$$
\vec{F} = -\frac{GMm}{r^2} \hat{r}
$$

and numerically integrate its motion using a time step loop.

---

## 💻 Python Code for 2D Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11
M = 5.972e24
R_earth = 6.371e6

# Time settings
dt = 1.0  # seconds
steps = 15000

# Initial Conditions
x = R_earth + 400000  # 400 km altitude
y = 0
vx = 0
vy = 7700  # close to circular orbital speed (m/s)

positions_x = []
positions_y = []

for _ in range(steps):
    r = np.sqrt(x**2 + y**2)
    ax = -G * M * x / r**3
    ay = -G * M * y / r**3

    vx += ax * dt
    vy += ay * dt
    x += vx * dt
    y += vy * dt

    positions_x.append(x)
    positions_y.append(y)

# Plotting
plt.figure(figsize=(8, 8))
plt.plot(positions_x, positions_y, label="Payload Trajectory")
circle = plt.Circle((0, 0), R_earth, color='b', fill=True, label="Earth")
plt.gca().add_patch(circle)
plt.xlabel("X Position (m)")
plt.ylabel("Y Position (m)")
plt.title("Simulated Trajectory of Released Payload")
plt.axis('equal')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()
```

---

## 📊 Visualization

- Trajectory curve will show if it's orbital or escape
- Earth is shown as a blue circle for reference

---

## 🚀 Real-World Applications

- Determining if satellites will stay in orbit or fall back to Earth
- Planning reentry maneuvers and escape trajectories
- Ensuring safe deployment of payloads from spacecraft

---

## ✅ Conclusion

This problem illustrates how gravitational forces shape the motion of free-falling objects in space. Through simulation and energy analysis, engineers can design efficient and safe missions for both orbital insertion and escape scenarios.
