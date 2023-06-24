---
layout: article
title: Introduction to fMRI
mathjax: true
tags: intro fmri physics
---

Our brain activity is constantly fluctuating as we engage in different activities on a daily basis. In fact, the brain is quite active even while we are resting with our eyes closed. fMRI is a safe and non-invasive neuroimaging tool that plays quite an essential in understanding brain activity and brain function. The discovery that a change in neuronal activity is associated with a change in local blood flow patterns which in turn leads to a change in blood's magnetic properties is the  fundamental idea behind how fMRI works.[^1] The [YouTube video](https://www.youtube.com/watch?v=P7EqyM1Ar_U) made by the Beckman Institute at UIUC is a useful first introduction to what an fMRI does.

### Blood Oxygen Level Dependent (BOLD) signal
Brain function requires glucose as an energy source. Hemoglobin transports oxygen to the brain which is required for glucose metabolism (which in turn releases energy). Regional brain function leads to blood flow which in turn changes the amount of oxygen in the neighborhood i.e. the local magnetic field is perturbed. This change in the amount of oxygen-induced by neural activity gives rise to the BOLD signal. A detailed description is given in the next paragraph.

![bold](/images/bold_signal.png)

1. In 1931, Linus Pauling discovered that the [magnetic properties](https://www.stanfordmagnets.com/whats-magnetic-moment.html) of hemoglobin in oxygenated and deoxygenated blood are different.[^2] 
    * Oxygenated hemoglobin is diamagnetic (individual atoms have no magnetic moment hence there is no net magnetic moment).
    * Deoxygenated blood is paramagnetic (atoms have random magnetic moment directions and hence there is a net magnetic moment).
2. When there is neuronal activity, there is an initial local oxygen consumption which means that the concentration of deoxyhemoglobin increases locally. This leads to a decrease in BOLD signal called *initial dip* or *fast response*.
3. However, due to the increase in demand for oxygen, an increased blood flow is observed in order to increase the concentration of oxygenated hemoglobin locally.
4. After a few seconds, delivery of oxygenated hemoglobin exceeds the demand which increases local oxygenated hemoglobin concentration significantly ($\approx$ 1 to 3 \% above baseline). This gives rise to a BOLD signal that is much stronger than the initial dip.

Therefore, the BOLD signal can be interpreted as **quantifying regional neuronal activity**.






[^1]: What is fMRI?, [Oxford Centre for Functional MRI of the Brain](https://www.ndcn.ox.ac.uk/divisions/fmrib/what-is-fmri)
[^2]: Ramani, Ramachandran (ed.), Functional MRI: Basic Principles and Emerging Clinical Applications for Anesthesiology and the Neurological Sciences, 1 (New York, 2018; online edn, Oxford Academic, 1 Jan. 2019)


