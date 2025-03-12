# Problem 1
<<<<<<< HEAD
# Analysis and Simulation of Projectile Motion
=======
>>>>>>> 7dff775783124a7001c0923d5da12e00015b3ff7

## 1. Theoretical Foundation
Projectile motion is governed by Newton's laws of motion and can be analyzed using kinematic equations. The equations of motion for a projectile launched with an initial velocity v0 at an angle θ from the horizontal are:

### Equations of Motion
- **Horizontal Motion:**
  x(t) = v0 * cos(θ) * t
- **Vertical Motion:**
  y(t) = v0 * sin(θ) * t - (1/2) * g * t^2

where:
- x(t) and y(t) are the horizontal and vertical positions as functions of time,
- v0 is the initial velocity,
- θ is the launch angle,
- g is the gravitational acceleration.

### Family of Solutions
The trajectory varies with different initial conditions. For a fixed v0, varying θ results in different parabolic paths. The maximum range occurs at θ = 45° in an idealized environment without air resistance.

## 2. Analysis of the Range
The horizontal range R of a projectile is given by:
R = (v0^2 * sin(2θ)) / g

### Influence of Parameters:
- **Angle of Projection:** Maximum range occurs at 45°, with symmetrical reduction on either side.
- **Initial Velocity:** Higher velocities increase range quadratically.
- **Gravity:** Stronger gravitational fields reduce range.

## 3. Practical Applications
This model extends to real-world applications, including:
- **Ballistics:** Predicting projectile paths in military and sports scenarios.
- **Engineering:** Estimating parabolic trajectories in bridge construction.
- **Astrophysics:** Calculating orbital insertions where gravity varies.

## 4. Implementation
To simulate projectile motion computationally, a Python script is developed to:
- Compute projectile trajectories for different v0 and θ.
- Graph the range versus angle of projection.

"""

import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, theta, g=9.81):
    """Computes the projectile range given initial velocity and angle."""
    return (v0 ** 2) * np.sin(2 * np.radians(theta)) / g

# Parameters
v0 = 20  # Initial velocity in m/s
theta_values = np.linspace(0, 90, 100)
ranges = [projectile_range(v0, theta) for theta in theta_values]

# Plot
plt.figure(figsize=(8, 5))
plt.plot(theta_values, ranges, label=f'v0={v0} m/s')
plt.xlabel('Angle (degrees)')
plt.ylabel('Range (m)')
plt.title('Projectile Range vs. Angle')
plt.legend()
plt.grid()
plt.show()

"""
### Limitations & Extensions
- **Limitations:**
  - Ignores air resistance, spin, and wind effects.
  - Assumes uniform gravity.
- **Extensions:**
  - Incorporate drag force using differential equations.
  - Model wind influence and uneven terrain effects.

## Conclusion
This study explored projectile motion through theoretical derivation, analytical range analysis, real-world applications, and computational simulation. The idealized model offers insight into fundamental motion principles while encouraging further refinements for real-world complexity.


