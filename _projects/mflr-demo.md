---
layout: page
title: Multifidelity Linear Regression (MFLR) Demo
description: Live interactive visualization of the surface pressure field upon a hypersonic vehicle, calculated on-the-fly by MFLR methods.
img: assets/img/example_image.png
importance: 2
category: research
---

This app is a demonstration of the multi-fidelity linear regression methods presented in my [work](https://arc.aiaa.org/doi/abs/10.2514/6.2023-0916). Due to the fast inference capability of the underlying linear regression based methodologies, we can enable live visualizations of the surface pressure field upon a hypersonic vehicle. When a user changes the parameters, the surface pressure field is updated live and the rendering reflects the changes! One can change between the multi-fidelity (multi-step) and single-fidelity methods to see the differences based on flight conditions.

{% include figure.liquid loading="eager" path="assets/img/example_image.png" title="MFLR Demo" class="img-fluid rounded z-depth-1" %}

<div style="display: flex; justify-content: center; gap: 10px; margin-top: 20px;">
  <a href="https://doi.org/10.2514/6.2023-0916" style="background-color: #dda0dd; color: white; padding: 10px; border-radius: 5px; text-decoration: none; font-size: 12px; display: inline-block; width: 50px; text-align: center;">DOI</a>
  <a href="https://www.researchgate.net/profile/Anirban-Chaudhuri-4/publication/367312344_Projection-based_multifidelity_linear_regression_for_data-poor_applications/links/63e3d1acdea6121757931091/Projection-based-multifidelity-linear-regression-for-data-poor-applications.pdf" style="background-color: #d3d3d3; color: black; padding: 10px; border-radius: 5px; text-decoration: none; font-size: 12px; display: inline-block; width: 50px; text-align: center;">PDF</a>
  <a href="https://github.com/VigneshSella/MFLR_Demo2" style="background-color: #454343; color: white; padding: 10px; border-radius: 5px; text-decoration: none; font-size: 12px; display: inline-block; width: 60px; text-align: center;">GitHub</a>
</div>
