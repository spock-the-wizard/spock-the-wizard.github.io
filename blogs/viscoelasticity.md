---
layout: page
permalink: /blogs/viscoelasticity/index.html
title: Viscoelasticity
---

# Viscoelasticity
<!-- ## 2024-Fall 英国硕士项目申请实录 -->

<!-- > **申请哲学：好好努力，心平气和，静候佳音**
>
> 更新时间：2023/03/02 -->


Viscoelastic materials are a combination of elastic and viscous materials.

## Difference to elastic materials

A key difference between viscoelastic and elastic materials is its response to loading and unloading of stress. Unlike elastic materials for which the process is reversible, the  process involves a hysteresis loop, meaning it is history-dependent. The difference between the stress when loading and unloading represents the amount of energy that is lost via heat.

What causes the difference in behavior? Viscoelastic materials are composed of molecules that rearrange themselves to accomodate stress. This rearrangement is what causes **creep**, which is the slowing down of flow at constant stress.

Some viscoelastic materials may undergo permanent deformation (a.k.a plastic deformation) when the amont of stress exceeds a certain threshold. Materials that undergo permananent deformation without a disctinctive threshold are classified as viscoplastic materials, which we do not discuss here.

## Linear and Non-linear viscoelasticity

For elastic materials, the relation between stress and strain is linear, and characterized by Young’s modulus E, which represents the rise over run of the stress-strain curve.

$$
\sigma = E \epsilon
$$

The specific formula for strain and stress for viscoelastic materials depends on whether the material is linear or non-linear.

Linear viscoelasticity is found in objects with small deformation:

$$
\epsilon = \frac{\sigma}{E} + \int^t_0 K(t-t')\dot\sigma(t')\,dt',
$$

$$
\sigma(t) = E\epsilon(t) + \int^t_0 F(t-t')\dot\epsilon(t')\,dt',
$$

where K is the creep function and F is the relaxation function.

For non-linear viscoelastic materials, the relation between stress and strain does not apply. It is more suitable for when the material undergoes large deformations.

<!-- <aside>
💡 what is the relaxation function?
</aside> -->

## Constitutive models of linear viscoelasticity

Constitutive models are models that capture the response of materials under different amounts of stress. 

They represent viscoelasticity with a combination of springs - for elasticity - and dampers - for viscosity. Each model differs in the arrangement of these components. The stress-strain relationship for the spring is:

$$
\sigma = E\epsilon
$$

The stress-strain relationship for the dashpot is:

$$
\sigma = \eta\frac{d\epsilon}{dt}
$$

<!-- <aside> -->
> They can also be expressed in terms of electrical circuits, with the following semantic correspondence (Electric - Mechanic):
> 
> - Current - Stress
> - Voltage - Strain rate
> - Inductance - Elastic modulus of spring
> - Resistance - Viscosity of dashpot
> 
<!-- 💡 what is the relaxation function? -->
<!-- </aside> -->

Two funamental models are Maxwell and Kelvin-Voigt models, which are two component models with a single dashpot and spring arranged in series and parallel, respectively.

More complicated models can be obtained by adding more components in series or parallel. (Standard linear solid model, Jeffreys model, Burgers model, Generalized Maxwell model)

## Constitutive models for non-linear viscoelasticity
    - TODO
    
## Traits of viscoelasticity


Two traits of viscoelastic materials are
[Stress Relaxation](https://en.wikipedia.org/wiki/Stress_relaxation)
and 
[Creep](https://en.wikipedia.org/wiki/Creep_(deformation)).

Stress-relaxation is the decrease in stress caused by change in strain.

Creep is a constant stress with an increased amount of strain, but the slowing down of deformation. Many models exist for modeling creep.

### Further Reading
  - https://en.wikipedia.org/wiki/Newtonian_fluid#
  - https://en.wikipedia.org/wiki/Second-order_fluid
  - https://en.wikipedia.org/wiki/Viscoplasticity#Phenomenology