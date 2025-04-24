# Problem 1

### **Gravity: Orbital Period and Orbital Radius**

#### **Motivation**
Kepler’s Third Law states that the square of the orbital period ($T^2$) is proportional to the cube of the orbital radius ($r^3$). This fundamental relationship provides critical insights into celestial mechanics, governing planetary orbits, satellite motion, and gravitational interactions on both small and cosmic scales. Understanding this law allows astronomers to determine planetary masses, calculate distances in space, and analyze the stability of orbits.

---

### **Derivation of Kepler's Third Law**
For a body in a circular orbit around a massive central body (e.g., a planet orbiting a star), the centripetal force required to maintain the orbit is provided by gravitational attraction:

$$
F_{\text{gravity}} = F_{\text{centripetal}}
$$

$$
\frac{G M m}{r^2} = \frac{m v^2}{r}
$$

Since the orbital velocity $v$ is related to the period $T$ by:

$$
v = \frac{2\pi r}{T}
$$

Substituting this into the equation:

$$
\frac{G M m}{r^2} = \frac{m (2\pi r)^2}{T^2 r}
$$

Canceling $m$ and simplifying:

$$
\frac{G M}{r^2} = \frac{4\pi^2 r}{T^2}
$$

Rearranging:

$$
T^2 = \frac{4\pi^2}{G M} r^3
$$

This confirms that $T^2 \propto r^3$, meaning the square of the orbital period is proportional to the cube of the orbital radius.

---

### **Implications in Astronomy**
- **Planetary Mass Calculation:** Given the orbital period and radius of a planet's moon, one can estimate the planet’s mass using Kepler’s Law.
- **Solar System Analysis:** The law allows astronomers to determine distances between planets and their stars even without direct measurements.
- **Satellite Orbits:** Understanding this relationship helps in designing stable satellite trajectories for communication and observation.
- **Exoplanet Detection:** By measuring periodic changes in a star’s brightness due to transiting planets, scientists can infer planetary orbits.

---

### **Real-World Examples**
#### **1. The Moon’s Orbit Around Earth**
- The Moon orbits Earth at an average radius of $3.84 \times 10^5$ km with a period of 27.3 days.
- Using Kepler’s Law, we can estimate Earth's mass and verify astronomical models.

#### **2. The Solar System**
- The orbits of planets around the Sun follow Kepler’s Third Law, with larger orbits corresponding to longer periods.
- For example:
  - **Earth:** $r = 1$ AU, $T = 1$ year
  - **Mars:** $r \approx 1.52$ AU, $T \approx 1.88$ years
  - **Jupiter:** $r \approx 5.2$ AU, $T \approx 11.86$ years

---

### **Computational Simulation**
To visualize the orbital relationship, we employ Python simulations:

1. **Circular Orbit Simulation:** 
   - Generates a circular path for an orbiting body.
   - Marks the central mass.

```python
import matplotlib.pyplot as plt
import numpy as np

# Orbital period (T) in Earth years and average orbital radius (r) in AU for each planet
# Data from NASA sources
planets = {
    "Mercury": {"T": 0.240846, "r": 0.387},
    "Venus": {"T": 0.615, "r": 0.723},
    "Earth": {"T": 1.0, "r": 1.0},
    "Mars": {"T": 1.881, "r": 1.524},
}

# Calculate T^2 and r^3 for each planet
T_squared = [data["T"] ** 2 for data in planets.values()]
r_cubed = [data["r"] ** 3 for data in planets.values()]
labels = list(planets.keys())

# Fit a linear regression line to the data (T^2 = k * r^3)
coefficients = np.polyfit(r_cubed, T_squared, 1)
k, b = coefficients

# Generate line for the fit
r_cubed_line = np.linspace(min(r_cubed), max(r_cubed), 100)
T_squared_line = k * r_cubed_line + b

# Plot the data points and the regression line
plt.figure(figsize=(8, 6))
plt.scatter(r_cubed, T_squared, color='blue', label='Planets')

# Add labels for each point
for i, label in enumerate(labels):
    plt.text(r_cubed[i] + 0.005, T_squared[i], label, fontsize=9)

# Plot the fitted line
plt.plot(r_cubed_line, T_squared_line, color='red', linestyle='--', label=f'Fit: $T^2 = {k:.2f}r^3 + {b:.2f}$')

plt.title(r"$T^2$ vs $r^3$ for Inner Planets with Kepler's Law Line")
plt.xlabel(r"$r^3$ (AU$^3$)")
plt.ylabel(r"$T^2$ (years$^2$)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
```

![alt text](6e91a65f-391b-4e5e-b553-ec1d031ae717.png)

3. **Animated Orbit Visualization:** 
   - Creates a dynamic representation of an object moving in a circular orbit.
   - Helps in understanding real-time orbital mechanics.

[Colab](https://colab.research.google.com/drive/1icEuLRckKuaCduUnGgaJcfvencpriOC_?usp=sharing)

---

### **Extension to Elliptical Orbits**
While Kepler’s Third Law is derived for circular orbits, it holds for elliptical orbits as well, with the semi-major axis $a$ replacing the orbital radius $r$:

$$
T^2 \propto a^3
$$

This extends the application of the law to non-circular celestial bodies, including exoplanets, binary star systems, and asteroids.

---

### **Conclusion**
Kepler’s Third Law serves as a powerful tool in celestial mechanics, linking orbital periods and radii in a predictable manner. By leveraging computational models and real-world observations, scientists continue to explore planetary systems, enhance satellite technology, and unravel the mysteries of the universe.