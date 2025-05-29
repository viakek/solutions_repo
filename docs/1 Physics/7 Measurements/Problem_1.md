# Problem 1

# **Measuring Earth's Gravitational Acceleration with a Pendulum**

## **Motivation**

Understanding the acceleration due to gravity, $g$, is vital for applications in physics and engineering. This experiment uses a modified pendulum—a key attached to a necklace—to determine $g$ through oscillation timing. The setup highlights the impact of experimental design and measurement precision.


## **Materials**

* Necklace length: $0.200 \pm 0.005 \, \text{m}$
* Weight: Key (\~30 g)
* Stopwatch (smartphone): Resolution ±0.01 s
* Ruler: Resolution ±0.005 m


## **Setup**

* **Length of pendulum**: $L = 0.200 \pm 0.005 \, \text{m}$
  *(Measured from pivot point to the center of mass of the key)*
* **Angle of release**: Less than 15° to satisfy the simple harmonic motion (SHM) condition


## **Data Collection**

Time recorded for **10 full oscillations**, repeated **10 times**:

| Trial | Time for 10 Oscillations (s) |
| ----- | ---------------------------- |
| 1     | 10.02                        |
| 2     | 9.90                         |
| 3     | 10.09                        |
| 4     | 9.86                         |
| 5     | 10.08                        |
| 6     | 9.76                         |
| 7     | 9.87                         |
| 8     | 10.23                        |
| 9     | 10.10                        |
| 10    | 9.76                         |


## **Calculations**

### **1. Mean Time:**

$$
\bar{t} = \frac{1}{10} \sum t_i = \frac{99.67}{10} = 9.967 \, \text{s}
$$

### **2. Standard Deviation:**

$$
\sigma = \sqrt{\frac{1}{n-1} \sum (t_i - \bar{t})^2} \approx 0.159 \, \text{s}
$$

### **3. Uncertainty in Mean:**

$$
u_t = \frac{\sigma}{\sqrt{10}} \approx 0.050 \, \text{s}
$$


### **4. Period of the Pendulum:**

$$
T = \frac{\bar{t}}{10} = \frac{9.967}{10} = 0.9967 \, \text{s}
$$

$$
u_T = \frac{u_t}{10} = 0.0050 \, \text{s}
$$


### **5. Gravitational Acceleration:**

$$
g = \frac{4\pi^2L}{T^2} = \frac{4\pi^2 \cdot 0.2}{(0.9967)^2} \approx 7.95 \, \text{m/s}^2
$$


### **6. Uncertainty in $g$:**

$$
\frac{u_g}{g} = \sqrt{\left(\frac{0.005}{0.2}\right)^2 + \left(2 \cdot \frac{0.0050}{0.9967} \right)^2} \approx 0.02696
$$

$$
u_g = 0.02696 \cdot 7.95 \approx 0.21 \, \text{m/s}^2
$$


## Final Result:

$$
\boxed{g = 7.95 \pm 0.21 \, \text{m/s}^2}
$$

## **Analysis and Discussion**

### **Comparison with Standard Value:**

* **Standard value**: $9.81 \, \text{m/s}^2$
* **Measured value**: $7.95 \pm 0.21 \, \text{m/s}^2$
* **Difference**: $\approx 1.86 \, \text{m/s}^2$
* Result is **outside experimental uncertainty**

### **Possible Sources of Error:**

* **Short pendulum** increases sensitivity to timing errors
* **Center of mass** of key-necklace system may not be well defined
* **Air resistance** and necklace flexibility may dampen motion
* **Angle of swing** may have been too large, violating SHM conditions


## **Suggestions for Improvement**

* Use a **stiff string or rod** to keep the length consistent
* Attach mass firmly to prevent swinging inconsistencies
* Use a **photogate or light sensor** to reduce timing errors
* Repeat at **multiple lengths** to verify results with a $T^2$ vs. $L$ graph


## **Conclusion**

Using a key attached to a necklace as a pendulum, the gravitational acceleration was measured as:

$$
\boxed{g = 7.95 \pm 0.21 \, \text{m/s}^2}
$$

Though the method is simple and accessible, the result deviates from the standard value due to limitations in control and precision of the setup. This experiment illustrates how even basic designs require careful execution for accurate physical measurements.

