---
layout: page
permalink: /blogs/24_spongecake/index.html
title: Implementing the SpongeCake BSDF
---

# Implementing the SpongeCake BSDF
<!-- ## 2024-Fall 英国硕士项目申请实录 -->

> Date：2024/09/20


The Rough Dielectric BSDF is a material model representing an important class of real-world objects characterized by rough surfaces.
## The SGGX Distribution
Can you imagine how fake things would look if a surface was ...perfect?
By perfect, I mean a surface is smooth no matter how much you zoom in to it.

Real world surfaces are not like this. They have noisier alignments for whatever reasons: friction, imperfections in manufacturing, etc.
Hence, graphics researchers and engineers have developed technologies to make surfaces... less perfect, and more realistic!

Microflake theory (CITE) is a method of realistically rendering volumetric media.
To simulate light paths inside volumetric media, the following parameters need to be specified:
- *The phase function*: models the distribution of scattered light at each point in the medium (?).
- *The extinction coefficient* models the attenuation of light as it propagates through the medium.


## The SpongeCake BSDF
### Parameters

- microflake distribution
- roughness
- thickness
- extinction coefficient / albedo?
- eta

### Lobes

## Implementation
What do we need to implement?

1) The ```sample()``` function

2) `eval_pdf()`

: Determines whether the sample represents reflection or refraction with the following criteria:
```
reflect = cos_theta_i * cos_theta_o > 0.0
```
<!-- ## Sampling the BSDF  -->

구현해야하는 것은 두 개의 함수다. 바로 1) ```sample``` 과 2) ```eval_pdf``` 이다.
(```sample``` 의 리턴 값을 보면 weight 이라는 것이 있어 이 함수만 구현해주면 되는구나 했는데, 착각이었다.
Integrator 중 `ptracer` 의 `sample` 구현을 보니 ```sample``` 함수는 importance sampling 을 위해 필요하고, ```eval_pdf```가 최종 contribution 계산에 필요해 두개의 함수 모두 구현이 필요하다.)

### Accounting for Compression of Solid Angle due to Refraction

## Closing Thoughts
drjit 문법이 낯설어 디버깅에 시간이 오래 걸렸다. 
지금까지 파악한 것으로 drjit 은 빠른 병렬연산을 위한 라이브러리로, 내가 python 으로 작성한 것을 최적화된 kernel 코드로 바꿔주는 역할을 한다.
코드의 output 이 코드인 셈이다. 
symbolic evaluation 모드에서 결과를 출력할 수 없다는 에러가 많이 떴다. (관련 설명 및 링크)
Tensorflow 도 비슷한 방식으로 동작해서 디버깅이 어려웠던 기억이 있다.

### Tips for Debugging
1. 
```sample``` 함수 내에서 array를 디버깅하려면 `dr.print` 를 사용했다.

2. 
Start with basic integrators (e.g. `direct`) and basic lighting (e.g. point light)
Only when I used a combination of the `direct` integrator and a point light did I notice that the transmission lobe was faulty.

### List of Errors Encountered
`Unable to cast Python instance of type <class 'tuple'> to C++ type '?'`
...Tuples in Python use parentheses, not brackets..

### TODO
SpongeCake BSDF



Any feedback would be highly appreciated!