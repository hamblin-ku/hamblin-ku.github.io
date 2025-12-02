---
layout: page
title: Research
hide_description: true
---

# Current Research

## <u> AGNBoost: Expanding Color Selection with Machine Learning to identify IR AGN </u>

<p>Identifying active galactic nuclei (AGN) from photometry alone is notoriously challenging. UV-optical photometry is highly susceptible to dust obscuration, and even mid-IR color selections—while more robust—often sacrifice either reliability or completeness (e.g., Kirkpatrick+2023). The problem becomes particularly acute when working with sparse photometric coverage: star-forming galaxies (SFGs) can easily mimic the rising mid-IR power-law characteristic of AGN emission, as illustrated in the animated color-color plot below.</p>

<p>Traditional color selection is essentially a rudimentary classification algorithm that draws decision boundaries in 2-D color space. AGNBoost extends this concept to higher dimensions, leveraging all available spectral information through machine learning. The key innovation is using <strong>distributional regression</strong> via XGBoostLSS (März 2019) to simultaneously predict two quantities: <strong>frac<sub>AGN</sub></strong> (the fraction of 3–30 μm mid-IR emission attributable to AGN) and <strong>photometric redshift</strong>.</p>

<p>Unlike standard regression methods that only predict a single value (the conditional mean), XGBoostLSS predicts the <em>entire conditional distribution</em> for each target variable. This means AGNBoost naturally quantifies both the uncertainty in each prediction and the full range of plausible values—critical for AGN identification where degeneracies between SFGs and AGN are common.</p>

<p><strong>Key Features:</strong></p>
<ul>
  <li>Trained on 10<sup>6</sup> mock galaxies from CIGALE spanning z = 0.01–8.0</li>
  <li>Uses 11 JWST bands (7 NIRCam + 4 MIRI) plus 55 derived colors as inputs</li>
  <li>Achieves sub-1% outlier fractions on test data (0.19% for frac<sub>AGN</sub>, 0.63% for redshift)</li>
  <li>Processes catalogs of ~1000 galaxies in <strong>minutes</strong> (vs. hours-to-days for traditional SED fitting)</li>
  <li>Provides robust uncertainty estimates combining aleatoric, epistemic, and photometric uncertainties</li>
  <li>Handles missing photometric bands through integrated imputation methods</li>
</ul>

<p>AGNBoost is publicly available on <a href="https://github.com/hamblin-ku/AGNBoost" target="_blank">GitHub</a> and enables rapid AGN candidate identification in large JWST surveys—essential for efficient follow-up observations in the era of wide-field infrared astronomy. For more detail, please view the paper prepreint [arXiv:2506.03130](https://arxiv.org/abs/2506.03130) </p>


