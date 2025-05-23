# 🌍 Problem 1: Orbital Period and Orbital Radius

## 🎯 Motivation

The relationship between the square of the orbital period and the cube of the orbital radius, known as **Kepler's Third Law**, is a cornerstone of celestial mechanics. This relationship allows us to understand planetary orbits, satellite systems, and gravitational dynamics on a universal scale.

---

## 📚 Theory: Deriving Kepler's Third Law

We begin with Newton's Law of Universal Gravitation and the formula for centripetal force in circular motion.

**Gravitational force:**

$$
F = \frac{GMm}{R^2}
$$

**Centripetal force:**

$$
F = \frac{mv^2}{R}
$$

Equating the two:

$$
\frac{GMm}{R^2} = \frac{mv^2}{R} \Rightarrow v^2 = \frac{GM}{R}
$$

Substitute \( v = \frac{2\pi R}{T} \):

$$
\left(\frac{2\pi R}{T}\right)^2 = \frac{GM}{R}
$$

Solving for \( T \):

$$
T^2 = \frac{4\pi^2}{GM} R^3
$$

✅ **Conclusion**: \( T^2 \propto R^3 \)

---

## 🧠 Applications in Astronomy

This law is used to:

- Calculate planetary masses and orbital distances
- Predict satellite orbits (e.g., GPS, Moon)
- Understand exoplanet systems

### 🌕 Example: The Moon’s Orbit

- Orbital radius: \( R = 3.84 \times 10^8 \, \text{m} \)
- Period: \( T = 27.3 \, \text{days} \)

### ☀️ Earth around Sun

- Orbital radius: \( R = 1.5 \times 10^{11} \, \text{m} \)
- Period: \( T = 365.25 \, \text{days} \)

Both satisfy the law:

$$
\frac{T^2}{R^3} = \text{constant}
$$

---

## 💻 Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # gravitational constant
M = 1.989e30     # mass of the Sun

# Radii (m)
radii = np.linspace(1e9, 1.5e11, 100)
periods = np.sqrt((4 * np.pi**2 * radii**3) / (G * M))

# Plot
plt.figure(figsize=(8,6))
plt.plot(radii / 1e9, periods / (60*60*24))
plt.xlabel("Orbital Radius (x10^9 m)")
plt.ylabel("Orbital Period (days)")
plt.title("Kepler's Third Law: T² ∝ R³")
plt.grid(True)
plt.show()
```

---

## 📈 Graph


![Kepler Plot](_pics/kepler_plot.png)

---

## 🔁 Extension to Elliptical Orbits

Kepler's law also holds for **elliptical orbits** when using the **semi-major axis** \( a \) instead of \( R \):

$$
T^2 = \frac{4\pi^2}{GM} a^3
$$

This allows astronomers to analyze more complex planetary and satellite paths.

---

## ✅ Conclusion

Kepler's Third Law beautifully unifies gravity, motion, and astronomical observations. Our simulation confirms the proportionality between \( T^2 \) and \( R^3 \), enabling accurate prediction and understanding of orbital mechanics across the universe.

plt.savefig("kepler_plot.png")

