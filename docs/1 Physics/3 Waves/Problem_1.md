# 🌊 Interference Patterns on a Water Surface

This project simulates and visualizes the interference pattern formed by coherent wave sources located at the vertices of a square polygon.
## 🧮 Model

The displacement at a point (x, y) and time t due to a source at (xᵢ, yᵢ):
- ψᵢ(x, y, t) = A / √rᵢ * cos(k rᵢ - ω t)
- where rᵢ = √((x - xᵢ)² + (y - yᵢ)²)
- k = 2π / λ, ω = 2π f

Total displacement from four sources:
- Ψ(x, y, t) = Σ₁⁴ ψᵢ(x, y, t)


## 🏠 Step 1: Select a Regular Polygon

Let's choose a square centered at the origin (0,0) with side length 2d. The vertices are:
- S₁ = (d, d)
- S₂ = (d, -d)
- S₃ = (-d, -d)
- S₄ = (-d, d)

---

## 🌊 Step 2: Position the Sources

- Four point sources at the square's corners.
- All sources are coherent: same amplitude $A$, wavelength $\lambda$, frequency $f$, and phase $\phi=0$.

---

## 🔬 Step 3: Wave Equations

$$
\psi_i(x, y, t) = \frac{A}{\sqrt{r_i}} \cos(k r_i - \omega t)
$$
$$
r_i = \sqrt{(x - x_i)^2 + (y - y_i)^2}, \quad k = \frac{2\pi}{\lambda}, \quad \omega = 2\pi f
$$

---

## ➕ Step 4: Superposition of Waves

$$
\Psi(x, y, t) = A \sum_{i=1}^{4} \frac{1}{\sqrt{r_i}} \cos(k r_i - \omega t)
$$

---
---

## 📈 Step 5: Interference Analysis

At t=0:
- Ψ(x, y, 0) = A Σ₁⁴ (1/√rᵢ) * cos(k rᵢ)

- Constructive interference occurs when:
  - k(rᵢ - rⱼ) = 2π m
- Destructive interference occurs when:
  - k(rᵢ - rⱼ) = (2m+1)π

**Symmetry Insight:**
- At the center (0,0):
  - r₁ = r₂ = r₃ = r₄ = √2 d
  - Ψ(0,0,0) = 4 A / √(2 d) * cos(k √2 d)
  - Maximized when k √2 d = 2π m

- Along y=0:
  - r₁ = r₂ = √((x - d)² + d²)
  - r₃ = r₄ = √((x + d)² + d²)

---

## 🎨 Step 6: Visualization (Python)
```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
A, lambda_, f, d = 1, 1, 1, 2
k, omega = 2*np.pi/lambda_, 2*np.pi*f
x = np.linspace(-5, 5, 500)
y = np.linspace(-5, 5, 500)
X, Y = np.meshgrid(x, y)
r = [np.sqrt((X - dx)**2 + (Y - dy)**2) for dx, dy in [(d,d), (d,-d), (-d,-d), (-d,d)]]
Psi = sum(A / np.sqrt(ri) * np.cos(k * ri) for ri in r)

plt.figure(figsize=(8,8))
plt.contourf(X, Y, Psi, levels=200, cmap='RdBu')
plt.colorbar(label='Wave Displacement')
plt.title('Interference Pattern from Square Polygon')
plt.xlabel('x')
plt.ylabel('y')
plt.axis('equal')
plt.savefig('interference_pattern.png')
plt.show()