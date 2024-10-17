---
layout: page
permalink: /blogs/24_roughdielectric/index.html
title: Implementing the Rough Dielectric BSDF in Python
---

# (Re)Implementing the Rough Dielectric BSDF in Python
<!-- ## 2024-Fall 英国硕士项目申请实录 -->

> Date：2024/09/14


The Rough Dielectric BSDF is a material model representing an important class of real-world objects characterized by rough surfaces.
It's already provided as a default material in [Mitsuba](), the physically-based (differentiable) renderer.

[Link to C++ src](https://github.com/mitsuba-renderer/mitsuba3/blob/master/src/bsdfs/roughdielectric.cpp)

Still, I wanted to replicate the same algorithm in Python to familiarize myself with how to write custom plugins, because I am planning on implementing the [SpongeCake BSDF]() myself.

Here is the [link]() to my Python implementation. 

## Theory

### Background: Microfacet Theory
<!-- The world is full of imperfections. -->
Can you imagine how fake things would look if a surface was *perfect* ?
By perfect, I mean a surface is smooth no matter how much you zoom in to it.
They would probably look very fake, like this:

Real world surfaces are not like this. They have noisier alignments for whatever reasons: friction, imperfections in manufacturing, etc.
Hence, graphics researchers and engineers have developed technologies to make surfaces... less perfect, and more realistic!

high-level idea: surfaces are made of perfectly specular micro-facets. if we account for the fact that some of the facets are "misaligned" with the macroscopic geometry normal, we can achieve a much realistic appearance!

Statistical, rather than explicit.
We don't want to increase the rendering cost too much. For example, we wouldn't want to model the geometry of the individual facets.
Instead, we can represent the alignment statistically, using normal distribution functions (NDFs).

Our 주인공 today, the rough dielectric BSDF, implements microfacet models.
Let's look at the detailed form.

### The Rough Dielectric BSDF
I will briefly talk about the role of eac
f_s = DFG / 4()()

### Importance Sampling

## Implementation
TODO
<!-- 
### The core logic

Integrator 중 `ptracer` 의 `sample` 구현을 보니 ```sample``` 함수는 importance sampling 을 위해 필요하고, ```eval_pdf```가 최종 contribution 계산에 필요해 두개의 함수 모두 구현이 필요하다.)

What do we need to implement?

### Step 1. ```sample()``` 

### Step 2. `eval_pdf()`

: Determines whether the sample represents reflection or refraction with the following criteria:
```
reflect = cos_theta_i * cos_theta_o > 0.0
```

구현해야하는 것은 두 개의 함수다. 바로 1) ```sample``` 과 2) ```eval_pdf``` 이다.
(```sample``` 의 리턴 값을 보면 weight 이라는 것이 있어 이 함수만 구현해주면 되는구나 했는데, 착각이었다.
Integrator 중 `ptracer` 의 `sample` 구현을 보니 ```sample``` 함수는 importance sampling 을 위해 필요하고, ```eval_pdf```가 최종 contribution 계산에 필요해 두개의 함수 모두 구현이 필요하다.)

### Accounting for Compression of Solid Angle due to Refraction

### Questions
- Wait, what about the diffuse term? Why is it all black?

&rarr; The rough dielectric BSDF is for specular reflection / transmission. To add diffuse colors, combine with XX.

### Tips for Debugging
1. 
```sample``` 함수 내에서 array를 디버깅하려면 `dr.print` 를 사용했다.

2. 
Start with basic integrators (e.g. `direct`) and basic lighting (e.g. point light)
Only when I used a combination of the `direct` integrator and a point light did I notice that the transmission lobe was faulty.

### List of Errors Encountered
`Unable to cast Python instance of type <class 'tuple'> to C++ type '?'`
...Tuples in Python use parentheses, not brackets..

## Closing Thoughts
drjit 문법이 낯설어 디버깅에 시간이 오래 걸렸다. 
지금까지 파악한 것으로 drjit 은 빠른 병렬연산을 위한 라이브러리로, 내가 python 으로 작성한 것을 최적화된 kernel 코드로 바꿔주는 역할을 한다.
코드의 output 이 코드인 셈이다. 
symbolic evaluation 모드에서 결과를 출력할 수 없다는 에러가 많이 떴다. (관련 설명 및 링크)
Tensorflow 도 비슷한 방식으로 동작해서 디버깅이 어려웠던 기억이 있다.

It took me an embarrassingly long time to implement this. 
I eventually ended up translating the C++ code line by line into Python because I couldn't find the bug.


Thank you for reading my first post! 
Any feedback would be highly appreciated!

... I will need to add a commentary section first. -->