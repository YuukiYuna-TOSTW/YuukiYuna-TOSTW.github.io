---
title: Calculus Study 4
date: 2025-06-12
categories: Study
tags: [Calculus,Numerical Integration]
image:
    path: assets/happy birthday Ganyu!.jpg
---

# About Numerical Integration

![fff]assets/Effective Math Assignments.jpg

Hello everyone, nice too meet you all again. In this side I will explain a littel math material that I learn today. After learning about the definition and usefullness from Numerical in calculus. now we will learn about the Numerical Integration. Why we have to learn about Numerical Integration ? That's because if we got a problem that not just a function, we have to use other method to solve the problem. Next I will show you all a littel Numerical integration that we mostly use in math problem,

![fff]assets/Banish Your Number Phobia With a Bit of Everyday Math.jpg

Numerical integration is a method used to compute the definite integral of a function, whether the function is given explicitly in the form of a mathematical expression or empirically through a table of values. The basic concept of definite integration is to calculate the area under the curve of a function $f(x)$ over an interval $[a, b]$. In practice, definite integrals are widely used in various fields of engineering and science, such as calculating the RMS (Root Mean Square) current in electrical circuits or the total heat absorbed from solar radiation.

Numerical integration methods can be classified into three main types: strip-based methods (or partition methods), Newton-Cotes methods, and Gaussian quadrature methods. In the strip method, the integration interval is divided into several equal-width strips, and the area of each strip is calculated and summed. Common rules under the strip method include the rectangle rule, trapezoidal rule, and midpoint rule. The rectangle rule uses the function value at one end of the strip, while the trapezoidal rule computes the area of the trapezoid formed by function values at both ends. The midpoint rule uses the function value at the center of the strip for approximation. These three rules have different levels of error, with the midpoint and trapezoidal rules having an error order of $O(h^2)$, which is more accurate than the rectangle rule.

The Newton-Cotes method uses polynomial interpolation to approximate the function being integrated. One of its popular forms is Simpson’s 1/3 rule, which employs a second-degree polynomial and requires three points to form a parabolic approximation. Simpson’s 1/3 rule provides more accurate results than the trapezoidal rule due to its higher error order of $O(h^4)$, but it requires an even number of strips. Each rule’s computation can be implemented algorithmically, as shown through procedural code examples in the material.

Finally, to achieve accurate results, it is essential to understand the error behavior of each method. The error refers to the difference between the exact integral value and the numerical approximation. Simpson’s 1/3 rule offers the highest level of accuracy among the methods discussed, making it ideal for applications requiring high precision—provided that the even-segment condition is met. This topic is crucial in computational engineering, science, and applied mathematics, especially when dealing with integration problems where the function is not explicitly available.