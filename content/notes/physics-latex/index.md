---
title: "Physics Equations with LaTeX Syntax"
date: 2024-08-27
# weight: 1
# aliases: ["/first"]
tags: ["LaTeX", "Physics", "Motion", "Equation"]
categories: ["notes"]
author: "behoovah"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: true
comments: false
# description: "Desc Text."
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: false
ShowWordCount: true
ShowRssButtonInSectionTermList: false
UseHugoToc: true
# cover:
  #  image: "<image path/url>" # image path/url
  #  alt: "<alt text>" # alt text
  #  caption: "<text>" # display caption under cover
  #  relative: false # when using page bundles set this to true
  #  hidden: true # only hide on current single page
# editPost:
  #  URL: "https://github.com/<path_to_repo>/content"
  #  Text: "Suggest Changes" # edit text
  #  appendFilePath: true # to append file path to Edit link
---
# Motion Equations

## Velocity

### Average Velocity
$$
\vec{v}=\frac{\Delta \vec{r}}{\Delta t}
$$
```
$$
\vec{v}=\frac{\Delta \vec{r}}{\Delta t}
$$
```
$$
unit: \frac{m}{s}
$$

### Instant Velocity
$$
\vec{v}=\frac{d\vec{r}}{dt}
$$
```
$$
\vec{v}=\frac{d\vec{r}}{dt}
$$
```
$$
unit: \frac{m}{s}
$$

## Acceleration
### Average Acceleration
$$
\vec{a}=\frac{\Delta \vec{v}}{\Delta t}
$$
```
$$
\vec{a}=\frac{\Delta \vec{v}}{\Delta t}
$$
```
### Instant Acceleration
$$
\vec{a}=\frac{d\vec{v}}{dt}
$$
```
$$
\vec{a}=\frac{d\vec{v}}{dt}
$$
```
$$
unit: \frac{m}{s^{2}}
$$

## Non-Uniform Motion
### Velocity
$$
v=\frac{ds}{dt}
$$
```
$$
v=\frac{ds}{dt}
$$
```
$$
\int_{s_i}^{s_f}ds=\int_{t_i}^{t_f}vdt
$$
```
$$
\int_{s_i}^{s_f}ds=\int_{t_i}^{t_f}vdt
$$
```
$$
s_f-s_i=\Delta s=\int_{t_i}^{t_f}vdt
$$

```
$$
s_f-s_i=\Delta s=\int_{t_i}^{t_f}vdt
$$
```
$$
s_f=s_it\int_{t_i}^{t_f}vdt
$$
```
$$
s_f=s_it\int_{t_i}^{t_f}vdt
$$
```
### Acceleration
$$
a=\frac{dv}{dt}
$$
```
$$
a=\frac{dv}{dt}
$$
```
$$
\int_{t_i}^{t_f}adt=\int_{v_i}^{v_f}dv
$$
```
$$
\int_{t_i}^{t_f}adt=\int_{v_i}^{v_f}dv
$$
```
$$
v_f-v_i=\int_{t_i}^{t_f}adt
$$
```
$$
v_f-v_i=\int_{t_i}^{t_f}adt
$$
```
$$
v_f=v_i+\int_{t_i}^{t_f}adt
$$
```
$$
v_f=v_i+\int_{t_i}^{t_f}adt
$$
```

## Vectors
$$
\vec{A}=\vec{A_x}+\vec{A_y}
$$
```
$$
\vec{A}=\vec{A_x}+\vec{A_y}
$$
```
### Unit Vectors
$$
\hat{i}\parallel x
$$
$$
\hat{j}\parallel y
$$
```
$$
\hat{i}\parallel x
$$
$$
\hat{j}\parallel y
$$
```
$$
\vec{A_x}=A_x\hat{i},   
$$
$$
\vec{A_y}=A_y\hat{j}
$$
```
$$
\vec{A_x}=A_x\hat{i},   
$$
$$
\vec{A_y}=A_y\hat{j}
$$
```

$$
\vec{A}=A_x\hat{i}+A_y\hat{j}
$$
```
$$
\vec{A}=A_x\vec{i}+A_y\vec{j}
$$
```
### Multiplication
#### Scaler
$$
\beta\vec{A}=\beta(A_x\hat{i}+A_y\hat{j})
$$
```
$$
\beta\vec{A}=\beta(A_x\hat{i}+A_y\hat{j})
$$
```
#### Dot Product
$$
\vec{A}\cdot\vec{B}=
$$
#### Cross Product
$$
\vec{A}\times\vec{B}=\vec{C}
$$
```
$$
\vec{A}\times\vec{B}=\vec{C}
$$
```
$$
|\vec{A}\times\vec{B}|=|\vec{A}||\vec{B}|sin(\alpha)=|\vec{C}|
$$
```
$$
|\vec{A}\times\vec{B}|=|\vec{A}||\vec{B}|sin(\alpha)=|\vec{C}|
$$
```

\(\odot\) : out of plane
\(\otimes\) : into plane

$$
if \vec{A}\parallel\vec{B} then \vec{C}=0
$$
cross product is always parallel to the two vectors.

## Kinematics (2D)
### Trajectory
Two deminsional: x&y motions(vertical and horizontal)

Smooth line graph-looks like an arc.

### Postion(vec) vs. Time(Scaler).

$$
\vec{r}=x\hat{i}+y\hat{j}
$$
### velocity
$$
\vec{v}=\frac{d\vec{r}}{dt}=\frac{dx}{dt}\hat{i}+\frac{dy}{dt}\hat{j}
$$
### Direction of Velocity?
e.g.
$$
\vec{v}=6\hat{i}+3\hat{j}
$$
Would be in the 1st quadrant.
$$
tan(\theta)=\frac{1}{2}
$$
so
$$
\theta = tan^-1 \frac{1}{2}
$$
slope of the trajectory arc (direction tangent to trajectory curve)
$$
tan(\theta)=\frac{\frac{dy}{dt}}{\frac{dx}{dt}}=\frac{dy}{dx}
$$

## Projectile motion
(No force other than gravity)

**Treat X & Y motions seperately**.

---
how fast it moves in the x direction has
no effect on motion in Y direction, and vice versa.

Y motion determines the time duration of the projectile motion.

**X motion**: constant velocity 

**Y motion**: free fall 

---

## Projectile Motion PT.2
---
A ball(B) is launched with initial speed of \(V_o\) the launch of
angle \(\theta\) can be varied. Determine \(\theta\) when l B is the largest

x-motion: uniform motion

$$
l=v_x, \Delta t
$$

\(\Delta t\): time of travel; \(V_x\) is a constant.
$$
V_x=V_0cos\theta
$$
$$
l=V_0cos\theta\Delta t
$$

---
If we can write \(l=f(\theta)\):
$$
\frac{df(\theta)}{d\theta}=0
$$
$$
f'(\theta)=0->
$$
solve for
$$
\theta
$$
Goal: to express \(\Delta t\) as a function of \(\theta\).

y-motion: Constant acceleration.(force of gravity)
$$
a_y=a_g=9.8m/s^2
$$
needed equations:
$$
V_(yf)=V_(yi)+a_y\Delta t
$$
$$
V_(yf^2)+2a_y\Delta y
$$
$$
\Delta y = V_yi \Delta t t \frac{1}{2}a_y \Delta t^2
$$
Use the third equation..

---

## Relative Motion

We discuss only uniform motions here.

eg. from c's perspective speed of B=1m/s
From A's perspective speed of B?
(3m/s)
speed of C=2m/s

Perspective = ***Reference Frame***

Nothing can move faster than the speed of light.
SO keeping it low speed.
### Reference Frame

Coordinate system where postion and velocity are measured.

Earth is the most important reference frame.

\(s'\) is another reference frame(e.g bus, boat etc.)



[go back](../).
