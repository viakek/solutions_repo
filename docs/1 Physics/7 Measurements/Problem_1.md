# Problem 1

# **Measuring Earth's Gravitational Acceleration with a Pendulum**

## **Motivation**

The acceleration due to gravity, $g$, is a fundamental constant in physics, playing a critical role in mechanics, astronomy, and engineering. One of the simplest yet effective methods to measure $g$ is by analyzing the motion of a simple pendulum. This experiment provides insight into precision measurement techniques and the treatment of uncertainties in experimental physics.


## **Materials**

* String (charger cable): 1.500 ± 0.005 m
* Weight: 30 g key
* Stopwatch (smartphone timer): Resolution ±0.01 s
* Ruler: Resolution ±0.005 m


## **Setup**

* Length of pendulum $L = 1.500 \pm 0.005 \, \text{m}$ (measured from suspension point to center of mass of the weight)
* Angle of release: < 15° to approximate simple harmonic motion


## **Data Collection**

Displaced the pendulum to a small angle and measured the time for 1 complete oscillation, repeated 10 times:

| Trial | Time for 1 Oscillation (s) |
| ----- | -------------------------- |
| 1     | 1.44                       |
| 2     | 1.33                       |
| 3     | 1.39                       |
| 4     | 1.32                       |
| 5     | 1.38                       |
| 6     | 1.26                       |
| 7     | 1.28                       |
| 8     | 1.20                       |
| 9     | 1.28                       |
| 10    | 1.29                       |

### Mean Time:

$$
\bar{t} = \frac{1}{10} \sum t_i = \frac{13.17}{10} = 1.317 \, \text{s}
$$

### Standard Deviation:

$$
\sigma = \sqrt{\frac{1}{n-1} \sum (t_i - \bar{t})^2} \approx 0.071 \, \text{s}
$$

### Uncertainty in Mean:

$$
u_t = \frac{\sigma}{\sqrt{n}} = \frac{0.071}{\sqrt{10}} \approx 0.022 \, \text{s}
$$


## **Calculations**

### 1. Period of the pendulum:

Since each measurement was for 1 oscillation,
$T = \bar{t} = 1.317 \, \text{s}$

$$
u_T = u_t = 0.022 \, \text{s}
$$


### 2. Gravitational acceleration:

Using the formula $g = \frac{4\pi^2L}{T^2}$

$$
g = \frac{4\pi^2 \cdot 1.500}{(1.317)^2} \approx \frac{59.218}{1.734} \approx 34.14 \, \text{m/s}^2
$$


### 3. Uncertainty in $g$:

$$
\frac{u_g}{g} = \sqrt{\left(\frac{u_L}{L}\right)^2 + \left(2 \cdot \frac{u_T}{T} \right)^2}
$$

$$
\frac{u_g}{g} = \sqrt{\left(\frac{0.005}{1.500}\right)^2 + \left(2 \cdot \frac{0.022}{1.317} \right)^2} \approx \sqrt{(0.0033)^2 + (0.0334)^2} \approx 0.0335
$$

$$
u_g = 0.0335 \cdot 34.14 \approx 1.14 \, \text{m/s}^2
$$

$$
\boxed{g = 34.14 \pm 1.14 \, \text{m/s}^2}
$$


## **Analysis and Discussion**

### Comparison with Standard Value:

* Standard value: $g = 9.81 \, \text{m/s}^2$
* Measured value: $34.14 \pm 1.14 \, \text{m/s}^2$
* Difference: 24.33 → **not within experimental uncertainty**

### Sources of Uncertainty:

* **Length measurement**: Key’s center of mass is hard to measure precisely
* **Assumption of SHM**: May not hold perfectly, especially with larger amplitudes
* **Air resistance and pivot friction**: Can affect period
* **Cable flexibility**: Stretching or swaying introduces error
* **Mass asymmetry**: Key is not a point mass or symmetrical


### Improvements:

* Use a more symmetrical and compact mass (e.g., metal sphere)
* Minimize angular displacement to <10°
* Use a rigid, non-stretchable string
* Use photogate/light gate for accurate timing
* Repeat with multiple lengths and plot $T^2$ vs. $L$


## **Conclusion**

By analyzing the period of a pendulum using a 30 g key and a 1.5 m charger cable, we attempted to determine the acceleration due to gravity. The measured value:

$$
\boxed{g = 34.14 \pm 1.14 \, \text{m/s}^2}
$$

significantly deviates from the accepted value. This discrepancy highlights the importance of appropriate materials, accurate measurements, and adherence to the assumptions of simple harmonic motion in pendulum experiments.

