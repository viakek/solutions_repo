# Problem 1
# Investigating the Range as a Function of the Angle of Projection

## Motivation
Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Beneath this simplicity lies a complex and versatile framework. The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

## Theoretical Foundation
To derive the governing equations of projectile motion, we start with Newton's equations of motion. Neglecting air resistance, the horizontal and vertical motions can be described separately:

- Horizontal motion: \( x = v_0 \cos(\theta) t \)
- Vertical motion: \( y = v_0 \sin(\theta) t - \frac{1}{2} g t^2 \)

where \( v_0 \) is the initial velocity, \( \theta \) is the launch angle, \( g \) is gravitational acceleration, and \( t \) is time.

By solving for the time of flight when the projectile returns to the ground $$ y = 0 $$ , we can derive the range equation:

$$
 R = \frac{v_0^2 \sin(2\theta)}{g}
$$

This equation shows that the range depends on the angle of projection, initial velocity, and gravity.

## Analysis of the Range
To analyze the range, we compute the horizontal displacement as a function of the launch angle. The range is maximized at an angle of 45 degrees, assuming a level launch and landing surface. We also investigate how variations in initial velocity and gravity affect the range.

## Practical Applications
The principles of projectile motion apply to various real-world scenarios, such as:

- **Sports Physics:** Understanding ball trajectories in soccer, basketball, and golf.
- **Engineering:** Designing ballistic trajectories for missiles and projectiles.
- **Space Exploration:** Calculating launch angles for rockets and planetary landers.

## Implementation
We implemented a Python script to simulate projectile motion and visualize the relationship between range and launch angle.

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(theta, v0, g=9.81):
    """
    Compute the range of a projectile given an initial velocity and launch angle.
    :param theta: Launch angle in degrees
    :param v0: Initial velocity (m/s)
    :param g: Gravitational acceleration (m/s^2), default is Earth's gravity
    :return: Range of the projectile (m)
    """
    theta_rad = np.radians(theta)
    return (v0 ** 2 * np.sin(2 * theta_rad)) / g

# Define parameters
v0 = 20  # Initial velocity in m/s
angles = np.linspace(0, 90, 100)  # Angle from 0 to 90 degrees
ranges = [projectile_range(theta, v0) for theta in angles]

# Plot the results
plt.figure(figsize=(10, 5))
plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
plt.xlabel("Angle of Projection (degrees)")
plt.ylabel("Range (m)")
plt.title("Projectile Range as a Function of Launch Angle")
plt.legend()
plt.grid()
plt.show()
```

## Results
The simulation confirms that the maximum range occurs at a 45-degree angle. The graph clearly illustrates how the range varies with launch angle, demonstrating the theoretical prediction.

## Discussion and Future Work
While this model provides a solid understanding of projectile motion, real-world conditions introduce additional complexities such as:

- **Air resistance:** Affects the range and trajectory.
- **Uneven terrain:** Impacts the landing position.
- **Wind effects:** Alters the motion path.

Future work could incorporate these factors to create a more comprehensive simulation of projectile motion.

## Conclusion
This analysis highlights the importance of launch angle in projectile motion. Through theoretical derivations, computational simulations, and graphical representations, we have demonstrated how different parameters influence the projectile's range. This study serves as a foundation for further investigations into more complex projectile dynamics.
