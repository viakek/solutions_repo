# Problem 1

# Electromagnetism: Simulating the Effects of the Lorentz Force

## Problem 1: Lorentz Force

### Motivation

The **Lorentz force**, given by:

$$
\vec{F} = q(\vec{E} + \vec{v} \times \vec{B}),
$$

describes the force acting on a charged particle in electric ($$\vec{E}$$) and magnetic ($$\vec{B}$$) fields. This principle is foundational in particle accelerators, plasma confinement systems, and devices like mass spectrometers.

Understanding and visualizing the trajectories resulting from this force helps in designing and interpreting physical systems where charged particles interact with electromagnetic fields.

---

## 1. Applications of the Lorentz Force

### Key Systems:
- **Particle Accelerators** – Use electric fields to accelerate and magnetic fields to steer particles.
- **Mass Spectrometers** – Use $$ \vec{v} \times \vec{B} $$ to separate particles by mass-to-charge ratio.
- **Plasma Confinement** (e.g., Tokamaks) – Use strong magnetic fields to confine plasma.

### Relevance of Fields:
- **Electric Fields ($$\vec{E}$$)**: Accelerate particles.
- **Magnetic Fields ($$\vec{B}$$)**: Curve particle paths, confine motion.

---

## 2. Simulating Particle Motion

### Parameters:
- Charge: $$ q = 1 \, \text{C} $$
- Mass: $$ m = 1 \, \text{g} = 0.001 \, \text{kg} $$

We solve the equations of motion:

$$
\frac{d\vec{v}}{dt} = \frac{q}{m}(\vec{E} + \vec{v} \times \vec{B}), \quad
\frac{d\vec{r}}{dt} = \vec{v}
$$

### Numerical Integration (RK4):

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Constants
q = 1  # Coulombs
m = 0.001  # kg
dt = 0.01
steps = 5000

# Fields
E = np.array([0.0, 0.0, 0.0])
B = np.array([0.0, 0.0, 1.0])

# Initial conditions
r = np.zeros((steps, 3))
v = np.zeros((steps, 3))
r[0] = np.array([0.0, 0.0, 0.0])
v[0] = np.array([1.0, 0.0, 0.0])  # Try other values for spirals, drifts, etc.

# RK4 integration
for i in range(steps - 1):
    def acc(v): return (q / m) * (E + np.cross(v, B))

    k1v = acc(v[i]) * dt
    k1r = v[i] * dt

    k2v = acc(v[i] + 0.5 * k1v) * dt
    k2r = (v[i] + 0.5 * k1v) * dt

    k3v = acc(v[i] + 0.5 * k2v) * dt
    k3r = (v[i] + 0.5 * k2v) * dt

    k4v = acc(v[i] + k3v) * dt
    k4r = (v[i] + k3v) * dt

    v[i + 1] = v[i] + (k1v + 2 * k2v + 2 * k3v + k4v) / 6
    r[i + 1] = r[i] + (k1r + 2 * k2r + 2 * k3r + k4r) / 6
```
## 3. Trajectory Scenarios

### A. Circular Motion (Uniform $$\vec{B}$$, No $$\vec{E}$$)

- **Initial condition**: Velocity is perpendicular to the magnetic field.
- **Expected trajectory**: Circle in the plane perpendicular to $$\vec{B}$$.

#### Physical Background

A charged particle in a uniform magnetic field experiences a centripetal force due to the Lorentz force:

$$
\vec{F} = q\vec{v} \times \vec{B}
$$

If $$\vec{v} \perp \vec{B}$$ and there is no electric field, the particle moves in a circle with radius:

$$
r_L = \frac{mv}{qB}
$$

and angular frequency:

$$
\omega_c = \frac{qB}{m}
$$

#### Python Simulation Code

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
q = 1.0        # Charge (C)
m = 0.001      # Mass (kg)
B = np.array([0, 0, 1.0])  # Magnetic field (T)
E = np.array([0, 0, 0])    # Electric field (V/m)
v0 = np.array([1.0, 0.0, 0.0])  # Initial velocity (m/s)
r0 = np.array([0.0, 0.0, 0.0])  # Initial position (m)
dt = 0.01
T = 10
N = int(T / dt)

# Initialize arrays
r = np.zeros((N, 3))
v = np.zeros((N, 3))
r[0] = r0
v[0] = v0

# Time evolution using Euler method
for i in range(N - 1):
    F = q * (E + np.cross(v[i], B))
    a = F / m
    v[i+1] = v[i] + a * dt
    r[i+1] = r[i] + v[i+1] * dt

# Plot trajectory
plt.figure(figsize=(6, 6))
plt.plot(r[:, 0], r[:, 1])
plt.title("Circular Trajectory in XY Plane")
plt.xlabel("x [m]")
plt.ylabel("y [m]")
plt.axis('equal')
plt.grid()
plt.show()
```

### B. Spiral in Z-direction

- **Initial condition**: Add a vertical velocity component $$v_z$$ to the initial velocity.
- **Expected trajectory**: Helical motion (spiral) around the magnetic field lines in the z-direction.

#### Physical Background

When a charged particle has a velocity component both **perpendicular** and **parallel** to a uniform magnetic field $$\vec{B}$$, it follows a **helical** path.

- Circular motion in the plane perpendicular to $$\vec{B}$$
- Constant drift along the direction of $$\vec{B}$$

This results in a **spiral trajectory** along the z-axis.

#### Python Simulation Code

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Constants
q = 1.0        # Charge (C)
m = 0.001      # Mass (kg)
B = np.array([0, 0, 1.0])  # Magnetic field (T)
E = np.array([0, 0, 0])    # Electric field (V/m)
v0 = np.array([1.0, 0.0, 0.5])  # Initial velocity with vz component
r0 = np.array([0.0, 0.0, 0.0])
dt = 0.01
T = 10
N = int(T / dt)

# Initialize arrays
r = np.zeros((N, 3))
v = np.zeros((N, 3))
r[0] = r0
v[0] = v0

# Time evolution using Euler method
for i in range(N - 1):
    F = q * (E + np.cross(v[i], B))
    a = F / m
    v[i+1] = v[i] + a * dt
    r[i+1] = r[i] + v[i+1] * dt

# Plot 3D trajectory
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot(r[:, 0], r[:, 1], r[:, 2])
ax.set_title("Helical (Spiral) Trajectory in 3D")
ax.set_xlabel("x [m]")
ax.set_ylabel("y [m]")
ax.set_zlabel("z [m]")
plt.show()
### B. Spiral in Z-direction

- **Initial condition**: Add a vertical velocity component $$v_z$$ to the initial velocity.
- **Expected trajectory**: Helical motion (spiral) around the magnetic field lines in the z-direction.

#### Physical Background

When a charged particle has a velocity component both **perpendicular** and **parallel** to a uniform magnetic field $$\vec{B}$$, it follows a **helical** path.

- Circular motion in the plane perpendicular to $$\vec{B}$$
- Constant drift along the direction of $$\vec{B}$$

This results in a **spiral trajectory** along the z-axis.

#### Python Simulation Code

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# Constants
q = 1.0        # Charge (C)
m = 0.001      # Mass (kg)
B = np.array([0, 0, 1.0])  # Magnetic field (T)
E = np.array([0, 0, 0])    # Electric field (V/m)
v0 = np.array([1.0, 0.0, 0.5])  # Initial velocity with vz component
r0 = np.array([0.0, 0.0, 0.0])
dt = 0.01
T = 10
N = int(T / dt)

# Initialize arrays
r = np.zeros((N, 3))
v = np.zeros((N, 3))
r[0] = r0
v[0] = v0

# Time evolution using Euler method
for i in range(N - 1):
    F = q * (E + np.cross(v[i], B))
    a = F / m
    v[i+1] = v[i] + a * dt
    r[i+1] = r[i] + v[i+1] * dt

# Plot 3D trajectory
fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot(r[:, 0], r[:, 1], r[:, 2])
ax.set_title("Helical (Spiral) Trajectory in 3D")
ax.set_xlabel("x [m]")
ax.set_ylabel("y [m]")
ax.set_zlabel("z [m]")
plt.show()
```
### C. Crossed Fields – Drift Motion

- **Field configuration**: Apply crossed electric and magnetic fields:
  
  $$
  \vec{E} = [1, 0, 0], \quad \vec{B} = [0, 0, 1]
  $$

- **Expected result**: The particle experiences a drift due to the cross product:

  $$
  \vec{v}_d = \frac{\vec{E} \times \vec{B}}{B^2}
  $$

This drift is perpendicular to both the electric and magnetic fields, causing the charged particle to move with a constant velocity in the $$y$$-direction while spiraling due to the magnetic field.

#### Python Simulation Code

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
q = 1.0        # Charge (C)
m = 0.001      # Mass (kg)
B = np.array([0, 0, 1.0])  # Magnetic field (T)
E = np.array([1.0, 0.0, 0.0])  # Electric field (V/m)
v0 = np.array([0.0, 1.0, 0.0])  # Initial velocity
r0 = np.array([0.0, 0.0, 0.0])
dt = 0.01
T = 10
N = int(T / dt)

# Initialize arrays
r = np.zeros((N, 3))
v = np.zeros((N, 3))
r[0] = r0
v[0] = v0

# Time evolution using Euler method
for i in range(N - 1):
    F = q * (E + np.cross(v[i], B))
    a = F / m
    v[i+1] = v[i] + a * dt
    r[i+1] = r[i] + v[i+1] * dt

# Plot 2D trajectory
plt.figure(figsize=(6, 6))
plt.plot(r[:, 0], r[:, 1])
plt.title("Drift Motion in XY Plane (Crossed E and B)")
plt.xlabel("x [m]")
plt.ylabel("y [m]")
plt.axis('equal')
plt.grid()
plt.show()
```
## 4. Parameter Exploration

### Parameters to Vary:

- Electric field $$\vec{E}$$ and magnetic field $$\vec{B}$$ strengths and directions
- Initial velocity vector $$\vec{v}_0$$
- Charge-to-mass ratio $$\frac{q}{m}$$

### Key Quantities to Observe:

- **Larmor radius** (radius of circular motion):

  $$
  r_L = \frac{mv_\perp}{qB}
  $$

- **Cyclotron frequency** (angular frequency of rotation):

  $$
  \omega_c = \frac{qB}{m}
  $$

- **Drift velocity** in crossed electric and magnetic fields:

  $$
  \vec{v}_d = \frac{\vec{E} \times \vec{B}}{B^2}
  $$

Use these analytical relationships to:

- Predict the trajectory before simulating.
- Compare numerical results to theoretical expectations.
- Validate your code's physical accuracy.

---

## 5. Real-World Relevance

| System               | Role of Lorentz Force                                            |
|----------------------|------------------------------------------------------------------|
| **Cyclotron**        | Charged particles move in circular paths under $$\vec{B}$$.      |
| **Mass Spectrometer**| Particle curvature $$\propto \frac{m}{q}$$ helps identify isotopes.|
| **Magnetic Bottle**  | Magnetic mirror effect traps particles via field gradients.      |
| **Solar Wind**       | Charged solar particles are deflected by Earth's magnetosphere.  |

These systems depend critically on the Lorentz force to manipulate, trap, or sort charged particles.

---

## 6. Extension Ideas

To make the simulation more advanced and realistic, consider exploring:

- **Non-uniform magnetic fields**  
  (e.g., magnetic mirrors, Earth's dipole field, magnetic bottles)

- **Time-varying electric fields**  
  (as seen in radio-frequency (RF) ion traps and linear accelerators)

- **Multiple interacting particles**  
  (introduce Coulomb forces to simulate plasma dynamics)

- **Relativistic effects**  
  (for particles approaching the speed of light, modify Newtonian dynamics)

- **Focusing and guiding mechanisms in accelerators**  
  (e.g., quadrupole magnets, beam optics)

These features reflect real-world complexities and provide stepping stones toward simulating full plasma systems, particle accelerators, and astrophysical plasmas.

---
