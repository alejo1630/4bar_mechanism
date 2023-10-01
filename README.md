# 4 bar Mechanism

This Python Notebook is a tool to calculate the kinematic model (position, velocity and acceleration) for a 4-bar mechanism in several configurations

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/4Bar.png" width = "500">

## 🔰 How does it work?

* User has to input the size of the 4 linkage bars $(a, b, c, d)$
* Linkage bars are classified based on their sizes
  * $S:$ Shortest member
  * $L:$ Longest member
  * $P, Q:$ Remaining members
* Grashof condition is applied in order to classify the 4-bar mechanism
### Grashof Mechanism
$$S + L < P + Q$$

* **Crank and Rocker Mechanism**: Occurs when the ground link $d$ is the shortest member $(S)$

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Crank_Rocker.png" width = "300">

* **Double Crank Mechanism**: Occurs when linkage bars $a$ or $c$ are the shortest member $(S)$

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Double_Crank.png" width = "250">

* **Double Rocker Mechanism**: Occurs when the couples link $b$ is the shortest member $(S)$

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Double_Rocker.png" width = "250">

### Triple Rocker Mechanism
$$S + L > P + Q$$

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Triple_Rocker.png" width = "300">

### Change Point State
$$S + L = P + Q$$

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Change_Point.png" width = "300">

* User hast to enter the initial angular position, angular velocity and angular acceleration. In addtion, time and time-step have to be defined.
* The kinematics models is derived using the vectorial representation of the 4 bar mechanism, getting the **Freudenstein's Equations**

### Position Analysis
Position analysis is performed solving the following equations. One of the three angles had to have been defined by the user, so it would be a system of two equations and two unknowns. 

**Real Part**

$$a\cos{\theta_2} + b\cos{\theta_3} - c\cos{\theta_4} - d = 0$$

**Imaginary Part**

$$a\sin{\theta_2} + b\sin{\theta_3} - c\sin{\theta_4} = 0$$

Due to the angles are related with trigonometric functions, Newton-Raphson method is used to solve the equations.

<img src = "https://github.com/alejo1630/4bar_mechanism/blob/main/example.gif" width = "500">


### Velocity Analysis

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Velocity.png" width = "500">

The velocity analysis is performed based on the following systems of linear equations

**Real Part**

$$-a\omega_2\sin{\theta_2} - b\omega_3\sin{\theta_3} + c\omega_4\sin{\theta_4} = 0$$

**Imaginary Part**

$$a\omega_2\cos{\theta_2} + b\omega_3\cos{\theta_3} - c\omega_4\cos{\theta_4} = 0$$


## Acceleration Analysis

<img src = "https://raw.githubusercontent.com/alejo1630/4bar_mechanism/main/Images/Acceleration.png" width = "500">

The acceleration analysis is performed based on the following systems of linear equations

**Real Part**

$$-a\alpha_2\sin{\theta_2}-a\omega_2^2\cos{\theta_2}-b\alpha_3\sin{\theta_3}-b\omega_3^2\cos{\theta_3}+c\alpha_4\sin{\theta_4}+c\omega_4^2\cos{\theta_4} = 0$$

**Imaginary Part**

$$a\alpha_2\cos{\theta_2}-a\omega_2^2\sin{\theta_2}+b\alpha_3\cos{\theta_3}-b\omega_3^2\sin{\theta_3}-c\alpha_4\cos{\theta_4}+c\omega_4^2\sin{\theta_4} = 0$$
