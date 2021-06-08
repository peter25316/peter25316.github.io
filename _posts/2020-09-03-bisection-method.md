---
layout: post
title: Bisection Method
subtitle: Numerical Analysis
gh-repo: peter25316
gh-badge: [follow]
tags: [math]
comments: true
---

## Solving Equation by Bisection Method
According to given information, each of the functions has exactly one root between -1 and 1. Therefore, f(-1)*f(1) < 0 and my starting interval is [-1, 1].

**(A) f(x) = (432x4 + 72x2 + 16x + 1)e − 8e6x**
          
| INTERVALS | ROOTS |
| :--- | :--- |
|[-1, 1] | -0.183513 |
|[-0.5, 1] | -0.183516 |
|[-0.5, 0] | -0.183513 |
|[-0.2, 0] | -0.183517 |
|[-0.19, -0.17] | -0.183515 |

f(-0.183515) = -1.5009e-04 ~ 0

After narrowing down the interval close to the approximated r. I am confident that the root is around -0.183515 since this is the root of the narrowest interval and when it is plugged in the function, the result is close to 0. Also, compared to other roots from outer intervals, only the last digit is different.

MATLAB Session:
~~~
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 1)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)
xc =  -0.183513641357422
>> xc = bisect(f,-0.5,1,0.0000005)
xc = -0.183516502380371
>> xc = bisect(f,-0.5,0,0.0000005)
xc =  -0.183513641357422
>> xc = bisect(f,-0.2,0,0.0000005)
xc =  -0.183517456054688
>> xc = bisect(f,-0.19,0.17,0.0000005)
xc =  -0.183515319824219
>> f(-0.183515)
ans = -1.5009e-04
~~~

**(B) f(x) = (432x4 + 72x2 + 16x + 2)e − 8e6x**

| INTERVALS | ROOTS |
| :--- | :--- |
|[-1, 1] | -0.135868 |
|[-0.5, 1] | -0.135869 |
|[-0.5, 0] | -0.135868 |
|[-0.2, 0] | -0.135867 |
|[-0.14, -0.13] | -0.135864 |

f(-0.135864) = -1.0840e-04 ~ 0

After narrowing down the interval close to the approximated r. I am confident that the root is around -0.135864 since this is the root of the narrowest interval and when it is plugged in the function, the result is close to 0. Also, compared to other roots from outer intervals, only the last digit is different.

MATLAB Session:
```
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 2)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)
xc =  -0.135868072509766
>> xc = bisect(f,-0.5,1,0.0000005)
xc =  -0.135869026184082
>> xc = bisect(f,-0.5,0,0.0000005)
xc =  -0.135868072509766
>> xc = bisect(f,-0.2,0,0.0000005)
xc =  -0.135867309570313
>> xc = bisect(f,-0.14,-0.13,0.0000005)
xc =  -0.135864257812500
>> f(-0.135864)
ans = -1.0840e-04
```

**(C) f(x) = (432x4 + 72x2 + 16x + 3)e − 8e6x**

| INTERVALS | ROOTS |
| :--- | :--- |
|[-1, 1] | 0.166992 |
|[-1, 0.5] | 0.166942 |
|[0, 0.5] | 0.166992 |
|[0, 0.2] | 0.166796 |
|[0.15, 0.17] | 0.166992 |

f(0.166992) = -3.5527e-15

I am not confident about my guess of the root of this function. Only the first 3 digits of the result agree with each other but after the 3rd digit, the number goes unpredicted. When I plugged 0.166992 into the function, because it is the result from the closest interval to the root, the result I got is extremely close to 0. I think this one is really hard to guess because the roots are inconsistent.

MATLAB Session:
```
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 3)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)
xc = 0.166992187500000
>> xc = bisect(f,-1,0.5,0.0000005)
xc = 0.166942596435547
>> xc = bisect(f,0,0.5,0.0000005)
xc = 0.166992187500000
>> xc = bisect(f,0,0.2,0.0000005)
xc = 0.166796875000000
>> xc = bisect(f,0.15,0.17,0.0000005)
xc = 0.166992187500000
>> f(0.166992)
ans = -3.5527e-15
```

**(D) f(x) = (432x4 + 72x2 + 16x + 4)e − 8e6x**

| INTERVALS | ROOTS |
| :--- | :--- |
|[-1, 1] | 0.436534 |
|[0, 1] | 0.436534 |
|[0, 0.5] | 0.436534 |
|[0.4, 0.5] | 0.436532 |

f(0.436532) = 1.8697e-04 ~ 0

After narrowing down the interval close to the approximated r. I am confident that the root is around 0.436532 since this is the root of the narrowest interval and when it is plugged in the function, the result is close to 0. Also, compared to other roots from outer intervals, only the last digit is different.

MATLAB Session:
```
>> f = @(x) (432*x^4 + 72*x^2 + 16*x + 4)*exp(1) - 8*exp(6*x);
>> xc = bisect(f,-1,1,0.0000005)
xc = 0.436534881591797
>> xc = bisect(f,0,1,0.0000005)
xc = 0.436534881591797
>> xc = bisect(f,0,0.5,0.0000005)
xc = 0.436534881591797
>> xc = bisect(f,0.4,0.5,0.0000005)
xc = 0.436532592773437
>> f(0.436532)
ans = 1.8697e-04
```

**MATLAB Code:**
```
%Program 1.1 Bisection Method
%Computes approximate solution of f(x)=0
%Input: function handle f; a,b such that f(a)*f(b)<0,
% and tolerance tol
%Output: Approximate solution xc
function xc = bisect(f,a,b,tol)
if sign(f(a)) * sign(f(b)) >= 0
error("f(a)f(b)<0 not satisfied!") %ceases execution
end
fa = f(a);
    	fb = f(b);
while (b - a) / 2 > tol
    	c = (a + b) / 2;
    	fc = f(c);
if fc == 0 %c is a solution, done
        		break
    	end    	
if sign(fc) * sign(fa)<0 %a and c make the new interval
        		b = c; fb = fc;
    	else %c and b make the new interval
        		a = c; fa = fc;
    	end
end
xc = (a + b) / 2; %new midpoint is best estimate
```