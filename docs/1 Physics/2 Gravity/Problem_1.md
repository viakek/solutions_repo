# Problem 1

# **Kepler's Third Law and Orbital Motion Report**  
### *Understanding the Relationship Between Orbital Period and Orbital Radius*  

## **Introduction**  
Kepler’s Third Law states that:  

"The square of the orbital period ($T^2$) of a planet is directly proportional to the cube of the semi-major axis ($r^3$) of its orbit."  

Mathematically, this is written as:  

$$
T^2 = \frac{4\pi^2 r^3}{G M}
$$

where:  
- $T$ = Orbital period (seconds)  
- $r$ = Orbital radius (meters)  
- $G$ = Gravitational constant ($6.67430 \times 10^{-11} m^3/kg/s^2$)  
- $M$ = Mass of the central body (kg)  

This law is fundamental in celestial mechanics, allowing astronomers to calculate planetary distances, satellite orbits, and even exoplanetary systems.

---

## **Derivation of Kepler’s Third Law**  
To derive Kepler’s Third Law, we start with the equation for **centripetal force**:

$$
F_c = \frac{M v^2}{r}
$$

For an object in orbit, this force is provided by gravity:

$$
F_g = \frac{G M m}{r^2}
$$

Since $F_c = F_g$, we equate:

$$
\frac{M v^2}{r} = \frac{G M m}{r^2}
$$

Solving for velocity $v$:

$$
v = \sqrt{\frac{G M}{r}}
$$

We use the relationship between velocity and orbital period:

$$
T = \frac{2\pi r}{v}
$$

Substituting $v$:

$$
T = \frac{2\pi r}{\sqrt{G M / r}}
$$

Squaring both sides:

$$
T^2 = \frac{4\pi^2 r^3}{G M}
$$

This confirms **Kepler’s Third Law**.

---

## **Implications in Astronomy**  
### **Calculating Planetary Distances**  
By knowing the period $T$, we can determine the distance $r$. This allows astronomers to:  
-Measure distances in our Solar System  
-Predict satellite behavior  
-Estimate exoplanet positions  

### **Real-World Examples**  
- **The Moon's Orbit**: Using Kepler’s Law, we can determine that the Moon’s orbital radius is about **384,400 km**.  
- **Planetary Orbits**: Astronomers used Kepler’s Law to confirm that **Neptune’s period (165 years) aligns with its distance from the Sun (30 AU)**.  

---

## **Visualizing the Relationship**  
Below is a **graphical representation** of Kepler’s Third Law:  

![Kepler's Law Graph](https://upload.wikimedia.org/wikipedia/commons/6/68/Kepler_Law_3_2nd_version-en.png)  

The graph shows that as the **orbital radius increases, the orbital period also increases**.

---

## **Orbital Simulation Video**  
A circular orbit simulation has been created to demonstrate planetary motion. **Watch the video here**:  

**[Download Orbit Simulation Video](orbit_simulation.mp4)**  

(*Ensure the file is in the same directory when opening in VS Code.*)  

---

## **Extending Kepler’s Law to Elliptical Orbits**  
While Kepler’s Third Law applies directly to **circular orbits**, it can also be used for **elliptical orbits** by replacing $r$ with the **semi-major axis** ($a$):

$$
T^2 \propto a^3
$$

This is crucial for calculating **comet trajectories and space probe paths**.

---

## **Conclusion**  
Kepler’s Third Law is a powerful tool in **gravitational physics and space exploration**. By analyzing the relationship between **orbital radius and period**, we can:  
-Predict planetary positions  
-Calculate satellite orbits  
-Study distant exoplanets  

This principle continues to be **a cornerstone of modern astronomy**