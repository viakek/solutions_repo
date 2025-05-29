# Problem 1

# **Measuring Earth's Gravitational Acceleration with a Pendulum**

## **Motivation**

The acceleration due to gravity, $g$, is a fundamental constant in physics. It is critical in many fields such as mechanics, astronomy, and engineering. This experiment explores a classical method for measuring $g$ by observing the oscillations of a simple pendulum, allowing for practice in measurement techniques and error analysis.

---

## **Materials**

* String (charging cable): $1.500 \pm 0.005 \, \text{m}$
* Weight: Metal key (mass \~30 g)
* Stopwatch (smartphone timer): Resolution ±0.01 s
* Ruler: Resolution ±0.005 m

---

## **Setup**

* **Length of pendulum** $L = 1.500 \pm 0.005 \, \text{m}$
  *(Measured from suspension point to center of mass of the key)*
* **Angle of release**: Less than 15°, to satisfy the small-angle approximation for simple harmonic motion.

---

## **Data Collection**

Measured the time for **10 complete oscillations**, repeated **10 times**:

| Trial | Time for 10 Oscillations (s) |
| ----- | ---------------------------- |
| 1     | 10.41                        |
| 2     | 10.75                        |
| 3     | 10.79                        |
| 4     | 10.87                        |
| 5     | 10.87                        |
| 6     | 10.56                        |
| 7     | 10.15                        |
| 8     | 10.17                        |
| 9     | 10.69                        |
| 10    | 10.80                        |

---

## **Calculations**

### **1. Mean Time:**

$$
\bar{t} = \frac{1}{10} \sum t_i = \frac{106.06}{10} = 10.606 \, \text{s}
$$

### **2. Standard Deviation:**

$$
\sigma = \sqrt{\frac{1}{n - 1} \sum (t_i - \bar{t})^2} \approx 0.274 \, \text{s}
$$

### **3. Uncertainty in Mean:**

$$
u_t = \frac{\sigma}{\sqrt{n}} = \frac{0.274}{\sqrt{10}} \approx 0.087 \, \text{s}
$$

---

## **1. Period of the Pendulum**

$$
T = \frac{\bar{t}}{10} = \frac{10.606}{10} = 1.0606 \, \text{s}
$$

$$
u_T = \frac{u_t}{10} = \frac{0.087}{10} = 0.0087 \, \text{s}
$$

---

## **2. Gravitational Acceleration**

Using the formula:

$$
g = \frac{4\pi^2L}{T^2}
$$

$$
g = \frac{4\pi^2 \cdot 1.5}{(1.0606)^2} \approx \frac{59.22}{1.126} \approx 52.64 \, \text{m/s}^2
$$

---

## **3. Uncertainty in $g$**

$$
\frac{u_g}{g} = \sqrt{\left(\frac{u_L}{L}\right)^2 + \left(2 \cdot \frac{u_T}{T} \right)^2}
$$

$$
\frac{u_g}{g} = \sqrt{\left(\frac{0.005}{1.500}\right)^2 + \left(2 \cdot \frac{0.0087}{1.0606} \right)^2} \approx 0.0167
$$

$$
u_g = 0.0167 \cdot 52.64 \approx 0.88 \, \text{m/s}^2
$$

$$
\boxed{g = 52.64 \pm 0.88 \, \text{m/s}^2}
$$

---

## **Analysis and Discussion**

### **Comparison with Standard Value:**

* **Standard value**: $g = 9.81 \, \text{m/s}^2$
* **Measured value**: $52.64 \pm 0.88 \, \text{m/s}^2$
* **Difference**: \~43 m/s² ⇒ **Not within experimental uncertainty**

### **Likely Sources of Error:**

* **Incorrect timing**: Possibly measured **5 oscillations**, not 10.
* **Length error**: Cable might have stretched or was not measured precisely to the center of mass.
* **Large swing amplitude**: Violates the small-angle assumption for SHM.
* **Timing human error**: Manual stopwatch use introduces delays.

---

## **Suggestions for Improvement**

* Use a **photogate or light gate** for accurate time measurement.
* Verify that the string is taut and measure **to the actual center of mass**.
* Repeat the experiment at **multiple lengths** and graph $T^2$ vs. $L$ to extract $g$ from the slope.
* Use a **smaller release angle** to ensure SHM approximation.

---

## **Conclusion**

Despite following a systematic method, the calculated value of gravity was significantly off due to likely timing or procedural errors. The result:

$$
\boxed{g = 52.64 \pm 0.88 \, \text{m/s}^2}
$$

does not align with the accepted value of $9.81 \, \text{m/s}^2$, showing that **accurate timing and careful setup are crucial** in pendulum experiments.
