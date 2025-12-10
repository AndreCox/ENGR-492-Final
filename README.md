# Final Exam Technical Report

## ENGR 492 - Finite Element Methods

**Author: Andre Cox**

## Problem Statement

For this final exam, we are tasked with determining the shape of a vertical bar that will experience a uniform axial stress as well as the shape that will cause stress that increases by a certain percentage along its length.

## Assumptions

- We assume that the bar is mounted vertically and is subject to its own weight.

- The material of the bar is uniform with no change of properties along its length.

- The bar does not experience any deformation.

## Governing Equations

We define $x=0$ as the bottom of the bar, and $x=L$ as the top of the bar.

The axial stress can be defined as
$$\sigma(x) = \frac{P(x)}{A(x)}$$

where $P(x)$ is the axial force at position $x$ and $A(x)$ is the cross-sectional area at position $x$.

The axial force at position $x$ is given by
$$P(x) = P_{applied} + \rho g \int_{x}^{L} A(x) dx$$
where $P_{applied}$ is the applied force at the top of the bar, $\rho$ is the density of the material, and $g$ is the acceleration due to gravity.

## Derivation of A(x)

We determine $A(x)$ which is the cross-sectional area at position $x$ along the bar. To derive this equation, we use the derivation covered in Lecture 3. This assumes that the stress remains constant so we use the force balance equation:

$\sigma_0A+\rho gAdx=\sigma(A+dA)$

This is then rearranged to get

$\frac{dA(x)}{A(x)}=\frac{\rho g}{\sigma_0}dx$

This is then integrated to get the final equation:
$A(x)=A_0exp(\frac{\rho g x}{\sigma_0})$

Where $A_0$ is the area at the bottom of the bar.

## Numerical method and disk formulation

To solve the problem numerically, we discretize the bar into a series of disks. The steps are as follows:

1. Compute the weight of the first disk element at the bottom using initial width and dx where dx = length / number of disks
2. Compute the stress at the bottom using applied force and area, we save this as our reference stress
3. Use the weight of the first disk to add to the applied force to get the total force at the next disk
4. compute the area at the next disk to keep the stress the same as the reference stress we do this using A = P / stress
5. Continue the process up the bar length

## Results for all disk counts

| 2 Disks                                           | 10 Disks                                            | 20 Disks                                            | 100 Disks                                             | 150 Disks                                             | 500 Disks                                             |
| ------------------------------------------------- | --------------------------------------------------- | --------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- | ----------------------------------------------------- |
| ![2 Disks](documentation/images/2_disks_area.png) | ![10 Disks](documentation/images/10_disks_area.png) | ![20 Disks](documentation/images/20_disks_area.png) | ![100 Disks](documentation/images/100_disks_area.png) | ![150 Disks](documentation/images/150_disks_area.png) | ![500 Disks](documentation/images/500_disks_area.png) |

## Verification of the Lecture 3 case

## Discussion

## Conclusion
