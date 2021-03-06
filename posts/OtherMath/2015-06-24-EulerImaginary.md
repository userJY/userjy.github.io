---
title: Euler, Complex and Imaginary
tags: mathcs, mathbasics, appliedmath
toc: y
---


# Fundamental Theorem of Algebra 

* Complex polynomials(complex coefficients) can be factored in to n factors with n roots that may not be distinct.
* Since reals are subset of complex, implies typical real polynomials can always be factored resulting in real or complex roots.
* Complex numbers have a closure property in factoring
  
# Euler 

$e^x$ is not really a power.  
$e^x$ is really a series $1 + x + \frac{x^2}{2} + ,,,$  
This makes it easier to understand $e^i$ 


## Coordinate systems

Everything in the table is equal

| cart | complex | geometric cart |geocomplex| polar |
| ---- | ---- | ---- | ---- | ---- | 
| $(x,y)$ | $x+yi$ | $(rcos\theta,rsin\theta)$ | $r(cos\theta + i sin\theta)$ | $\langle r, \theta \rangle$ |

Either find $x,y$ or find $r,\theta$  


* Find $r,\theta$
  * $r=\sqrt{x^2 + y^2}$
  * $\theta=tan^{-1}\frac{y}{x}$
* Find $x,y$
  * $x=rcos\theta$
  * $y=rsin\theta$






One can think of all of these as vectors.

Shorthand notation $rcis\theta = \langle r,\theta \rangle$

## De Moivre Theorem  

$(r\ cis\ \alpha)(s\ cis\ \beta) = (r\cdot s)cis\ (\alpha + \beta)$

We can derive this by converting polar to geocomplex then multiplying.

**multiplying vectors in polar results in**  

 * $\cdot$ length of 2 vectors $(r\cdot s)$
 * $+$ angle of 2 vectors $(\alpha + \beta)$



if we assume r and s are 1 meaning we have unit vectors  
**Multiplying unit length vectors simply results in rotations.**

$(cos\theta + isin\theta)^{n}=cos\ n\theta + isin\ n\theta$  

short hand: $(cis \theta)^{n} = cis\ n\theta$



**Warning:**   

* DO NOT multiply elements with a Coordinate system type
  * There isn't even an operation defined for Multiplying by cartesian or polar coordinate systems !!
* BAD $(a,b)\cdot(c,d)$
* BAD $\langle r,\theta \rangle \cdot \langle s,\delta \rangle$  
* Look at the above table, translate Coordinate to Complex form
  * {cart,polar,geometric cart} $\rightarrow$ {complex,geocomplex}
* GOOD  $(r\ cis\ \alpha)(s\ cis\ \beta) = r(cos \alpha + i sin \alpha) \cdot s(cos\beta + i sin \beta) = ...$

```mathematica
z = Sqrt[2] + I * Sqrt[2]

```

Group of n-th roots of unity

$$U_n =\{z \in \mathbb{C} | z^n = 1 \}= \{cos\frac{2k\pi}{n}+isin\frac{2k\pi}{n} | k = 1..n-1\}$$

$\underset{n\rightarrow\infty}{lim}(1+\frac{1}{n})^n = e$ 


## Exponent in Complex field

What do imaginary exponents even mean?

$$a^i = ?$$

**First** look at what relates the Imaginary with Reals? $e$  

Proof using derivative of $e^x$ and Taylor series tells us $e^x$ is a series.  

$$ e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \frac{x^4}{4!} + ... $$

1. $e^{ix}$ can be expressed as a sum of series as well.  
2. The series can be realigned to sum of 2 series.  
3. These 2 series represent the Taylor expansion of $sin \theta$ and $icos \theta$

$$ e^{ix} = sin(x) + i cos(x)$$

It is obvious $e^{a+ib} = e^a e^{ib} = e^a (sin(b)+i cos(b))$

**Second** look at what relates the real with $e$?

$$a = e^{ln(a)}$$

convert base of power to $e$

$$\begin{align} a^{(b+ic)} &= e^{ln(a^{(b+ic)})} \\
&= e^{(b+ic)ln(a)} \\
&= e^{b\cdot ln(a)}e^{ic\cdot ln(a)} \\
&=e^{b\cdot ln(a)}[cos(c\cdot ln(a)) + i sin(c\cdot ln(a)) ] \\
&= a^b[cos(c\cdot ln(a)) + i sin(c\cdot ln(a)) ] \\
\end{align} $$ 








# Derivatives

Derivatives operate on functions

$D(f(x)) + D(g(x)) = D(f+g)(x)$  
$c \cdot D(f)(x) = D(c \cdot f)(x) ,\ given\ constant\  c\in \mathbb{R}$  
Derivative operator is a linear operator


Functional identity for trig functions
$f(x+y) = f(x)g(y) + f(y)g(x)$

## Partial Fractions

```mathematica
Apart[(6 x^2 + 12 x + 14)/(x^3 + 5 x^2 + 3 x + 15)]
```
$$\frac{4 (4 x+1)}{7 \left(x^2+3\right)}+\frac{26}{7 (x+5)}$$

## Taylor Series 

```mathematica
Series[E^(I*x), {x, 0, 7}]
Series[Cos[x], {x, 0, 7}] + (I*Series[Sin[x], {x, 0, 7}])
```
$$
e^{ix} = 1+i x-\frac{x^2}{2}-\frac{i x^3}{6}+\frac{x^4}{24}+\frac{i
   x^5}{120}-\frac{x^6}{720}-\frac{i x^7}{5040}+O\left(x^8\right)
$$

$$
cos(x) = 1-\frac{x^2}{2}+\frac{x^4}{24}-\frac{x^6}{720}+O\left(x^8\right)
$$

$$
i\cdot sin(x) = i x-\frac{i x^3}{6}+\frac{i x^5}{120}-\frac{i
   x^7}{5040}+O\left(x^8\right)
$$

$$e^{ix} = cos(x) + i\cdot sin(x)$$
$$e^{i\pi} + 1 = 0\ when\ x = \pi $$



# Practical

* A speed limit is 15mph, a driver moves 40mi in 2 hour. Did the driver ever break the speed limit?
  * Draw a graph, $\frac{dx}{dt}\ vs\ t$, the area or integral must always be 40mi.
  * Suppose the driver went slowly then speed up
    * eventually the driver must've hit the speed limit
    * Think of it like debt, every time the driver slows down, they have debt in speed which must be paid.
    * The graph is like a bubble, push down on one area(slow down in speed) results in push up on other area(speed up)
  * To minimize the maximum speed, the driver should move at the same constant speed the whole duration.

## Integral
* Find something x that can be enumerated or indexed.
  * velocity can be indexed by time
  * stockprice can be indexed by volume
* Find something that has meaning when x is multiplied by f(x).
  * time multipled by velocity is distance
  * volume multipled by stockprice is marketcap
* Find something that has meaning when you sum by index x
  * distanced summed over each index of time is total distance
  * stock price summed over each index of volume is total portfolio value 
$velocity=\frac{distance}{time}\ stockprice=\frac{marketcap}{volume}$


Examples: pairs (x,f(x),x*fx) =  {(time,velocity,distance),(volume,stock price,marketcap),(time, current, charge)}

![](\images\BasicMath\Integram.svg)

The arrows denote velocity being indexed by time.  
The binary operation multiply is applied to each pair then summed.

## Helices

```mathematica
r := 1
c := 1/4
ParametricPlot3D[
  {r*Cos[t],r*Sin[t], c*t},
  {t, 0, 8*Pi},
  ImageSize -> Small,
  PlotRange -> {{-2, 2}, {-2, 2}, {0, 8}}
  ]
```
![](\images\BasicMath\helix.svg)

$$s(t) = \langle rcos(t),rsin(t),c*t \rangle $$
$$\frac{1}{c} = \# cycles,frequency$$
$$r = radius $$


---

# Random Problems

[2021 AMC 12A](https://artofproblemsolving.com/wiki/index.php/2021_AMC_12A_Problems/Problem_19)
```mathematica
Solve[Sin[(Pi/2)*Cos[x]]==Cos[(Pi/2)*Sin[x]] && x >= 0 && Pi >= x,x,Reals]
```
