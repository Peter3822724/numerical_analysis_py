[Applied Mathematics](https://en.wikipedia.org/wiki/Applied_mathematics)| [Numerical Analysis](https://en.wikipedia.org/wiki/Numerical_analysis])

# Introduction 
>  I choose to upload the python file for my CW in year 2, which including some main numerical methods for mathematical problems, like root-finding problem, linear system, interpolation, derivative of interpolation and ODE solver. 
>
> Additionaly, I add some interesting problems from physics, with my solutions by python and corresponding physics background. These problems could be used as case study for scientific computing learning by python.

+ ```orbitCalculator.py```
+ ```trinityExplosion.py```
+ ```fieldsVisualize.py```
+ 



# Background 

## Orbit for satellite 

```orbitCalculator.py``` 

According to the  Kepler's laws, the orbit is an ellipse with major axis $a$ and minor axis $b$, satisfying the formula:

$$
\frac{x^2}{a^2}+\frac{y^2}{b^2} = 1
$$
![p1](https://github.com/Peter3822724/numerical_analysis_py/blob/main/graph/IMG_0855.jpg)



$$
a=(h_1+h_2+2R)/2
$$

$$
c=h_2+R-a=(h_2-h_1)/2
$$

$$
b=\sqrt{a^2-c^2}
$$



The length of the orbit is :
$$
L=4\int_0^{\pi/2}\sqrt{x^2+y^2}d\theta=4\int_0^{\pi/2}\sqrt{a^2cos^2\theta+b^2sin^2\theta}d\theta
$$


The area for the satellite passing by in time unit is:

$$
s=\frac{\pi ab}{T}
$$
The average speed of satellite is:

$$
v = L/T
$$


The maximum speed of satellite is:

$$
v_{max}=\frac{2s}{h_1+R}​
$$
Some physical variables:

$h_1=200km$

$h_2=51000km$

$R=6378km$

$T=16 h$



## Trinity Explosion

```trinityExplosion.py```

[G. I. Taylor](https://en.wikipedia.org/wiki/G._I._Taylor) studied the movie of the Trinity test explosion, estimating the yield of the bomb. The method he used is what we called [dimension analysis](https://en.wikipedia.org/wiki/Dimensional_analysis).



![trinity](https://github.com/Peter3822724/numerical_analysis_py/blob/main/graph/trinity.png)



Dimensions of some physical variables:

$r$​ : the radius of the bomb cloud ~ $[L]$

$\rho$: density of air ~ $[ML^{-3}]$

$E$: energy released by the device ~ $[ML^2T^{-2}]$

$t$: time at which the bomb cloud reaches $r$ ~ $[T]$



Assuming that $r = f (\rho,E,t)$, that is :$r = C\rho^xE^yt^z$, where $x,y,z$ are constants. Based on their dimension:



$$
L = [ML^{-3}]^x[ML^2T^{-2}]^y[T]^z
$$


Expand both sides and equate corresponding exponents:

$$
L: 1 = -3x+2y \\
M:0 = x + y   \\
T: 0 = -2y + z \\
$$
solve this systems and we can get:

$$
x = -1/5, y = 1/5, z = 2/5
$$
we could get the relationship between these variables:

$$
r = C(\frac{t^2E}{\rho})^{1/5}
$$




we could also use linear regression to solve the constants by rewirte the model and fit it:



$$
r = at^b
$$
take the $log$ for both sides:
$$
log(r) = log(a) + blog(t)
$$
```trinityExplosion.py```  will calculate the parameter for $a$​ and $b$​ based on the data recorded.



$b \approx 0.4094$



so $E \approx \rho e^c$​, where $c = 5log(r)-2log(t)$​



By calculation, $E \approx 8.6418 \times10^{13} J$​, since $1 kt = 4.1848 \times 10 ^{12}$​, the total yield for bomb is $20.65 kt$​​.



## Fields Visualization

```fieldsVisualize.py```

For given function $Z=f(x,y)$​, we will show the contour plot with the direction fields as well.



The gradient provides the directions, which is given by:

$$
\frac{\partial f}{\partial x}i+\frac{\partial f}{\partial y}j
$$
The vector has a magnitude:

$$
\sqrt{(\frac{\partial f}{\partial x})^2+(\frac{\partial f}{\partial y})^2}
$$
 and a direction:

$$
\theta = \tan^{-1} (\frac{\partial f / \partial y}{\partial f /\partial x})
$$
In this example, we use function $f(x,y)=y-x-2x^2-2xy-y^2$​



# References：

Johansson, Robert, Robert Johansson, and Suresh John. *Numerical Python*. Vol. 1. Apress, 2019.

Kincaid, David, David Ronald Kincaid, and Elliott Ward Cheney. *Numerical analysis: mathematics of scientific computing*. Vol. 2. American Mathematical Soc., 2009.

Chapra, Steven C. *Applied numerical methods with MATLAB for engineers and scientists*. McGraw-Hill Higher Education, 2008.

Sauer, Timothy. "Numerical Analysis Pearson Addison Wesley." (2006).

Burden, Richard L., and J. Douglas Faires. "Numerical analysis 8th ed." *Thomson Brooks/Cole* (2005).

喻文健. *数值分析与算法*. Qing hua da xue chu ban she, 2015.

https://blog.nuclearsecrecy.com/trinity/

