# Problem 1
# Investigating the Range as a Function of the Angle of Projection

## Motivation

Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Beneath this simplicity lies a complex and versatile framework involving both linear and quadratic relationships.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

---

## 1. Theoretical Foundation

The motion of a projectile is governed by Newton's laws of motion. Assuming no air resistance, the equations of motion in two dimensions are:

### Equations of Motion

Let:

 $$
 v_0 
$$ 
 
 be the initial velocity,

 $$
 theta 
 $$
 
  be the angle of projection,

$$
 g 
$$

 be the acceleration due to gravity.

The horizontal and vertical components of the initial velocity are:

$$
 v_{0x} = v_0 \cos(\theta) 
 $$

$$
 v_{0y} = v_0 \sin(\theta) 
 $$
 

The time of flight 

$$
 T 
 $$ 
 
 is given by:

$$
 T = \frac{2 v_0 \sin(\theta)}{g} 
 $$


The range 

$$ 
R 
$$ 

horizontal displacement when 

$$
 y = 0 
 $$

  is:

 $$
 R = \frac{v_0^2 \sin(2\theta)}{g} 
 $$

This equation shows that the range is maximized when 

$$
theta = 45^\circ 
$$



---

## 2. Analysis of the Range

The relationship between range and angle of projection can be analyzed by varying 

$$
theta 
  $$ 
 
 from 0° to 90°. Key observations:

- The range is **symmetric** about 45°.
- Maximum range occurs at **45°** for a given initial velocity.
- Increasing **initial velocity** increases the range quadratically.
- Higher **gravitational acceleration** reduces the range.

---

## 3. Practical Applications

This model can describe:
- The trajectory of a **soccer ball** or **basketball**.
- The motion of **missiles and rockets**.
- The effect of **uneven terrain** and **air resistance** on projectiles.

More realistic factors such as **air resistance**, **wind**, and **altitude variations** can be incorporated to refine the model.

---

## 4. Implementation: Python Simulation

Below is a Python script to visualize the range as a function of the angle of projection.

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g=9.81):
    angles = np.linspace(0, 90, 100)  # Angles in degrees
    angles_rad = np.radians(angles)   # Convert to radians
    ranges = (v0**2 * np.sin(2 * angles_rad)) / g
    
    plt.figure(figsize=(8,5))
    plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
    plt.xlabel('Angle (degrees)')
    plt.ylabel('Range (m)')
    plt.title('Projectile Range vs. Angle of Projection')
    plt.legend()
    plt.grid()
    plt.show()

# Example Usage
projectile_range(v0=20)
```
[simulation](index.html)
---

## 5. Discussion & Limitations

- The idealized model assumes **no air resistance**.
- In reality, drag force affects both horizontal and vertical motion.
- The effect of **wind** and **altitude differences** can significantly alter the trajectory.
- Real-world simulations may use **numerical integration** to handle complex cases.

---

## Conclusion

This investigation provides an insightful look into projectile motion and how range depends on the angle of projection. By understanding these principles, we can model real-world scenarios more effectively, from sports to engineering and space exploration.

