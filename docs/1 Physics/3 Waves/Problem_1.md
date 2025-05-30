# 🌊 Interference Patterns on a Water Surface

This project simulates and visualizes the interference pattern formed by coherent wave sources located at the vertices of a square polygon.

## 🧮 Model

The displacement at a point (x, y) and time t due to a source at (x_i, y_i):
- ψᵢ(x, y, t) = A / sqrt(rᵢ) * cos(k rᵢ - ω t)
- where rᵢ = sqrt((x - xᵢ)² + (y - yᵢ)²)
- k = 2π / λ
- ω = 2π f

Total displacement from four sources:
- Ψ(x, y, t) = Σ₁⁴ ψᵢ(x, y, t)

## 🏠 Step 1: Select a Regular Polygon

Let's choose a square centered at the origin (0,0) with side length 2d. The vertices are:
- S₁ = (d, d)
- S₂ = (d, -d)
- S₃ = (-d, -d)
- S₄ = (-d, d)

## 🌊 Step 2: Position the Sources

- Four point sources at the square’s corners.
- All sources are coherent: same amplitude A, wavelength λ, frequency f, and phase φ=0.

## 🔬 Step 3: Wave Equations

For each source:
- ψᵢ(x, y, t) = A / sqrt(rᵢ) * cos(k rᵢ - ω t)
- rᵢ = sqrt((x - xᵢ)² + (y - yᵢ)²)
- k = 2π / λ, ω = 2π f

## ➕ Step 4: Superposition of Waves

- Ψ(x, y, t) = A Σ₁⁴ 1/sqrt(rᵢ) * cos(k rᵢ - ω t)

## 📈 Step 5: Interference Analysis

At t=0:
- Ψ(x, y, 0) = A Σ₁⁴ 1/sqrt(rᵢ) * cos(k rᵢ)

- Constructive interference: k(rᵢ - rⱼ) = 2π m
- Destructive interference: k(rᵢ - rⱼ) = (2m+1)π

### 💡 Symmetry Insight
- At the center (0,0):
  - r₁ = r₂ = r₃ = r₄ = sqrt(2) d
  - Ψ(0,0,0) = 4 A / sqrt(2 d) * cos(k sqrt(2) d)
  - Maximized when k sqrt(2) d = 2π m

- Along y=0:
  - r₁ = r₂ = sqrt((x - d)² + d²)
  - r₃ = r₄ = sqrt((x + d)² + d²)

## 🎨 Step 6: Visualization (Python)
```python
import numpy as np
import matplotlib.pyplot as plt

A, lambda_, f, d = 1, 1, 1, 2
k, omega = 2*np.pi/lambda_, 2*np.pi*f
x = np.linspace(-5, 5, 500)
y = np.linspace(-5, 5, 500)
X, Y = np.meshgrid(x, y)
r = [np.sqrt((X - dx)**2 + (Y - dy)**2) for dx, dy in [(d,d), (d,-d), (-d,-d), (-d,d)]]
Psi = sum(A/np.sqrt(ri) * np.cos(k*ri) for ri in r)

plt.figure(figsize=(8,8))
plt.contourf(X, Y, Psi, levels=200, cmap='RdBu')
plt.colorbar(label='Wave Displacement')
plt.title('Interference Pattern from Square Polygon')
plt.xlabel('x')
plt.ylabel('y')
plt.axis('equal')
plt.savefig('interference_pattern.png')
plt.show()