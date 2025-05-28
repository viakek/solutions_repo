# Problem 1

# **Measuring Earth's Gravitational Acceleration with a Pendulum**

## **Motivation**

The acceleration due to gravity, $g$, is a fundamental constant in physics, playing a critical role in mechanics, astronomy, and engineering. One of the simplest yet effective methods to measure $g$ is by analyzing the motion of a simple pendulum. This experiment provides insight into precision measurement techniques and the treatment of uncertainties in experimental physics.


## **Materials**

* String: 1.000 ± 0.005 m
* Weight: Metal washer
* Stopwatch (smartphone timer): Resolution ±0.01 s
* Ruler: Resolution ±0.005 m


## **Setup**

* Length of pendulum $L = 1.000 \pm 0.005 \, \text{m}$ (measured from suspension point to center of mass of the weight)
* Angle of release: < 15° to approximate simple harmonic motion


## **Data Collection**

Displaced the pendulum to a small angle and measured the time for 10 complete oscillations, repeated 10 times:

| Trial | Time for 10 Oscillations (s) |
| ----- | ---------------------------- |
| 1     | 20.11                        |
| 2     | 20.15                        |
| 3     | 20.12                        |
| 4     | 20.10                        |
| 5     | 20.13                        |
| 6     | 20.16                        |
| 7     | 20.14                        |
| 8     | 20.11                        |
| 9     | 20.12                        |
| 10    | 20.10                        |

### Mean Time:

$$
\bar{t} = \frac{1}{10} \sum t_i = \frac{201.14}{10} = 20.114 \, \text{s}
$$

### Standard Deviation:

$$
\sigma = \sqrt{\frac{1}{n-1} \sum (t_i - \bar{t})^2} \approx 0.021 \, \text{s}
$$

### Uncertainty in Mean:

$$
u_t = \frac{\sigma}{\sqrt{n}} = \frac{0.021}{\sqrt{10}} \approx 0.007 \, \text{s}
$$


## **Calculations**

### 1. Period of the pendulum:

$$
T = \frac{\bar{t}}{10} = \frac{20.114}{10} = 2.0114 \, \text{s}
$$

$$
u_T = \frac{u_t}{10} = \frac{0.007}{10} = 0.0007 \, \text{s}
$$

### 2. Gravitational acceleration:

Using the formula $g = \frac{4\pi^2L}{T^2}$

$$
g = \frac{4\pi^2 \cdot 1.000}{(2.0114)^2} \approx \frac{39.4784}{4.0458} \approx 9.76 \, \text{m/s}^2
$$

### 3. Uncertainty in $g$:

$$
\frac{u_g}{g} = \sqrt{\left(\frac{u_L}{L}\right)^2 + \left(2 \cdot \frac{u_T}{T} \right)^2}
$$

$$
\frac{u_g}{g} = \sqrt{\left(\frac{0.005}{1.000}\right)^2 + \left(2 \cdot \frac{0.0007}{2.0114} \right)^2} \approx \sqrt{(0.005)^2 + (0.0007)^2} \approx 0.0051
$$

$$
u_g = 0.0051 \cdot 9.76 \approx 0.05 \, \text{m/s}^2
$$

$$
\boxed{g = 9.76 \pm 0.05 \, \text{m/s}^2}
$$

---

## **Analysis and Discussion**

### Comparison with Standard Value:

* Standard value: $g = 9.81 \, \text{m/s}^2$
* Measured value: $9.76 \pm 0.05 \, \text{m/s}^2$
* Difference: 0.05 $\Rightarrow$ within experimental uncertainty

### Sources of Uncertainty:

* **Length measurement**: The most significant source due to ±0.005 m resolution
* **Assumption of SHM**: Only valid for small angles (<15°)
* **Air resistance and pivot friction**: Minor but present

### Improvements:

* Use a light gate or photogate timer for better timing accuracy
* Measure multiple lengths and plot $T^2$ vs. $L$ to find slope for $g$
* Use heavier mass to reduce air resistance effect


## **Conclusion**

By analyzing the period of a pendulum with careful timing and uncertainty analysis, we determined the acceleration due to gravity to be:

$$
\boxed{g = 9.76 \pm 0.05 \, \text{m/s}^2}
$$

This is in good agreement with the accepted standard value, demonstrating the effectiveness of the pendulum method in measuring gravitational acceleration.

