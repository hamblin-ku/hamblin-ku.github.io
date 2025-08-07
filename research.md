---
layout: page
title: Research
hide_description: true
---

# Current Research

## <u> AGNBoost: Expanding Color Selection with Machine Learning to identify IR AGN </u>

Identifying active galacic nulcei (AGN) from photometry alone can be, unfortunately, quite difficult. UV-Optical photometry is particularly succeptible to dust obscuration, and even mid-IR AGN color selections have been found to lack either reliability or completeness (e.g., Kirkpatrick+2023). When using just a few closely spaced photometric points, it is quite easy for star forming galaxies (SFGs) to mimic the rising mid-IR power-law characteristic of an AGN, as shown by the animated color-color plot below.

<div align="center">
<video controls style="max-width: 100%; height: auto;">
  <source src="/assets/video/sed_color_animation.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
</div>

Color selection is, already, a rudimentary classification algorithm (i.e., drawing a decision boundary in a 2-D space). It is logical then, to try to expand color-selection to higher dimensions, and make use of all available spectral information to perform the selection. Machine learning algorithms of various types are obvious candidates for such an approach, due to their inherent flexibility and modeling performance for tabular classification (or regression) tasks. 

AGNBoost expands on this idea with distributional regression via XGBoostLSS (März 2019), to predict $$frac_{AGN}$$, the fraction of mid-IR light attributable to an AGN, and photometric redshift. 

For more detail, please view the paper prepreint [arXiv:2506.03130](https://arxiv.org/abs/2506.03130)


