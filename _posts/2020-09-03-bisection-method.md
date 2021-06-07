---
layout: post
title: Bisection Method
subtitle: Numerical Analysis
gh-repo: peter25316
gh-badge: [follow]
---

## Solving Equation by Bisection Method
According to given information, each of the functions has exactly one root between -1 and 1. Therefore, f(-1)*f(1) < 0 and my starting interval is [-1, 1].

**(A) f(x) = (432x4 + 72x2 + 16x + 1)e − 8e6x**
          
| INTERVALS | ROOTS |
|:--- | :--- |
|[-1, 1] | -0.183513|
|[-0.5, 1] | -0.183516 |
|[-0.5, 0] | -0.183513 |
|[-0.2, 0] | -0.183517 |
|[-0.19, -0.17] | -0.183515 |

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |

f(-0.183515) = -1.5009e-04 ~ 0
After narrowing down the interval close to the approximated r. I am confident that the root is around -0.183515 since this is the root of the narrowest interval and when it is plugged in the function, the result is close to 0. Also, compared to other roots from outer intervals, only the last digit is different.
