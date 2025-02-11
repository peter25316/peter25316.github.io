---
layout: post
title: Floating Point Operations
subtitle: Numerical Analysis
gh-repo: peter25316
gh-badge: [follow]
---

## Is it possible for these errors to accumulate enough to significantly reduce the accuracy of solutions of systems of linear equations Ax = b. Worst case: Is it possible to lose all correct digits?

**Goal:**
- Check that the backward error of your answer is near machine epsilon, by multiplying _A_ times the output solution _x_ and comparing with your chosen _b_.
- Solve for _x_ with the smallest possible relative forward error (RFE). 

**A1(i, j) = (i + 1/ sin(i + j))/(j + cos(i + j) + 1)** 

|Size|RFE|RBE|EMF|Condition Number|
| --- | --- | --- | --- |
|6|8.992806499463768e-15 | 8.643437475739637e-16|10.404201481996878|59.051023822469567|
|12|1.887379141862766e-14|1.237560096703555e-15|15.250807996234771|7.219563930906002e+3|
|18|1.472155730652958e-13|8.280167659045603e-14|1.777929857549096|57.582507993251738|


MATLAB session:

n = 6:
```
>> geExample1
x = 1.000000000000002
    1.000000000000000
    0.999999999999997
    1.000000000000009
    0.999999999999999
    0.999999999999991

RFE = 8.992806499463768e-15

RBE = 8.643437475739637e-16

EMF = 10.404201481996878

>> cond(aorig, inf)

ans = 59.051023822469567
```

n = 12:
```
>> geExample1
x = 1.000000000000000
    1.000000000000002
    1.000000000000009
    0.999999999999995
    0.999999999999999
    1.000000000000009
    0.999999999999987
    0.999999999999985
    1.000000000000019
    1.000000000000000
    1.000000000000000
    1.000000000000003

RFE = 1.887379141862766e-14

RBE = 1.237560096703555e-15

EMF = 15.250807996234771

>> cond(aorig, inf)

ans = 7.219563930906002e+03
```

n = 18:
```
>> geExample1
x = 0.999999999999991
    0.999999999999986
    0.999999999999950
    0.999999999999979
    0.999999999999992
    0.999999999999961
    1.000000000000147
    1.000000000000085
    1.000000000000072
    1.000000000000013
    1.000000000000013
    1.000000000000012
    1.000000000000001
    1.000000000000004
    1.000000000000004
    1.000000000000006
    1.000000000000001
    1.000000000000003

RFE = 1.472155730652958e-13

RBE = 8.280167659045603e-14

EMF = 1.777929857549096

>> cond(aorig, inf)

ans = 57.582507993251738
```

**A2(i, j) = (i + sin(i + j))/(i + j + 1)**

|Size|RFE|RBE|EMF|Condition Number|
| --- | --- | --- | --- |
|6|3.889324418082651e-10|4.957930196870237e-16|7.844653441345022e+5|2.259665789391311e+6|
|12|2.415508971687075e-4|1.273150650140610e-15|1.897268772882690e+11|5.146361740838818e+12|
|18|22.666835057243510|3.610195135568162e-15|6.278562295407966e+15|2.663035149379290e+17|

MATLAB session:

n = 6:
```
>> geExample1
x = 1.000000000024352
    0.999999999870542
    1.000000000305901
    0.999999999611068
    1.000000000280725
    0.999999999904978

RFE = 3.889324418082651e-10

RBE = 4.957930196870237e-16

EMF = 7.844653441345022e+05

>> cond(aorig, inf)

ans = 2.259665789391311e+06
```
n = 12:
```
>> geExample1
x = 0.999999914764073
    1.000001345406795
    0.999990966405067
    1.000035545353396
    0.999906705296430
    1.000174187796226
    0.999761477619787
    1.000241550897169
    0.999821354056409
    1.000092633269657
    0.999969370155149
    1.000004950664436

RFE = 2.415508971687075e-04

RBE = 1.273150650140610e-15

EMF = 1.897268772882690e+11

>> cond(aorig, inf)

ans = 5.146361740838818e+12
```
n = 18:
```
>> geExample1
x = 0.999944880633007
    1.001080925079463
    0.991721661741099
    1.031083566678261
    0.961977041300073
    0.797832048577754
    2.336972703232886
   -3.343460966937534
   10.741783074414181
  -15.468876980644495
   22.727491584532771
  -21.666835057243510
   19.693596898123115
  -11.037199926451494
    6.886579062067647
   -1.073713777052164
    1.472930518037139
    0.947092606543897

RFE = 22.666835057243510

RBE = 3.610195135568162e-15

EMF = 6.278562295407966e+15

>> cond(aorig, inf)
Warning: Matrix is close to singular or badly scaled. Results may be inaccurate.
RCOND =  3.177575e-18. 
> In cond (line 46)

ans = 2.663035149379290e+17
```

**A3(i, j) = (i + sin(i + j))/(j + cos(i + j) + 1)**

|Size|RFE|RBE|EMF|Condition Number|
| --- | --- | --- | --- |
|6|4.485301019485632e-14|1.815908059128617e-16|2.470004467978380e+2|8.829339368344521e+2|
|12|2.722400083143839e-11|1.382817318709002e-16|1.968734442583834e+5|1.852023667474059e+6|
|18|9.979205684018666e-9|1.606602017114681e-16|6.211373804908112e+7|4.549076021914460e+8|



MATLAB session:

n = 6:
```
>> geExample1
x = 1.000000000000004
    1.000000000000000
    1.000000000000012
    0.999999999999973
    1.000000000000044
    0.999999999999955

RFE = 4.485301019485632e-14

RBE = 1.815908059128617e-16

EMF = 2.470004467978380e+02

>> cond(aorig, inf)

ans = 8.829339368344521e+02
```
n = 12:
```
>> geExample1
x = 0.999999999999857
    0.999999999999312
    0.999999999998766
    0.999999999997140
    0.999999999999233
    0.999999999990177
    0.999999999999798
    1.000000000003360
    0.999999999998826
    1.000000000015110
    0.999999999988805
    1.000000000027224

RFE = 2.722400083143839e-11

RBE = 1.382817318709002e-16

EMF = 1.968734442583834e+05

>> cond(aorig, inf)

ans = 1.852023667474059e+06
```
n = 18:
```
>> geExample1
x = 1.000000000000294
    0.999999999997227
    0.999999999993184
    0.999999999895639
    0.999999999500146
    0.999999998484185
    0.999999996688847
    0.999999995948169
    0.999999994349681
    0.999999993816509
    0.999999994028179
    0.999999997073929
    1.000000006084601
    1.000000006215319
    1.000000008930692
    1.000000009712359
    1.000000009979206
    1.000000009809144

RFE = 9.979205684018666e-09

RBE = 1.606602017114681e-16

EMF = 6.211373804908112e+07

>> cond(aorig, inf)

ans = 4.549076021914460e+08
```
**Conclusion:**
- Out of 9 matrics, 8 of them could be solved with at least some correct digits except for matrix A2 when n = 18. A2, when n = 18 was a total failure with 0 correct significant digits because of the result of its RFE, is ≈ 23 which is way larger than 0.5e-1.

- Ranking from easiest to solve to hardest: A1 > A3 > A2. A1 has 13 correct digits when n = 6, 13 when n = 12, 12 when n =18. For A2, it has 9 correct digits when n = 6, 3 when n = 12, 0 when n = 18. For A3, it has 13 correct digits when n = 6, 10 when n = 12, 8 when n = 18.

- For A1 and A3, n can be as large as 18 and still get at least one correct significant digit for the solution. A2 on the other hand, n can be only as large as 12 to get a good solution.

**MATLAB Code:**

Gauss elimination:
```
%%%% ELIMINATION
%n = 6;
for i = 1:n - 1
    for j = i + 1:n
        m = a(j, i) / a(i,i);
        for k = i:n
            a(j, k) = a(j, k) - m * a(i, k);
        end
        b(j) = b(j) - m * b(i);
    end
end
%%%% BACK-SUBSTITUTION
x = zeros(n, 1);
for i = n:-1:1
    for j = i + 1:n
        b(i) = b(i) - a(i, j) * x(j);
    end
    x(i) = b(i) / a(i, i);
end
x
```
examp1: where n is 6, 12 , and 18 and aorig is A1, A2,  and A3
```
n=18;
aorig = zeros(n,n); 
for i=1:n
    for j=1:n
        aorig(i,j) = (i + sin(i + j)) / ((i + j) + 1);
    end 
end
c = ones(n, 1);
borig = aorig * c;
a = aorig; b = borig;
gausselim
```