---
layout: article
title: Introduction to fMRI
mathjax: true
tags: intro fmri 
---

Our brain activity is constantly fluctuating as we engage in different activities on a daily basis. In fact, the brain is quite active even while we are resting with our eyes closed. fMRI is a safe and non-invasive neuroimaging tool that plays quite an essential in understanding brain activity and brain function. The discovery that a change in neuronal activity is associated with a change in local blood flow patterns which in turn leads to a change in blood's magnetic properties is the  fundamental idea behind how fMRI works.[^1] The [YouTube video](https://www.youtube.com/watch?v=P7EqyM1Ar_U) made by the Beckman Institute at UIUC is a useful first introduction to what an fMRI does.

### Blood Oxygen Level Dependent (BOLD) signal
Brain function requires glucose as an energy source. Hemoglobin transports oxygen to the brain which is required for glucose metabolism (which in turn releases energy). Regional brain function leads to blood flow which in turn changes the amount of oxygen in the neighborhood i.e. the local magnetic field is perturbed. This change in the amount of oxygen-induced by neural activity gives rise to the BOLD signal. A detailed description is given in the next paragraph.

![bold](/images/bold_signal.png)

1. In 1931, Linus Pauling discovered that the [magnetic properties](https://www.stanfordmagnets.com/whats-magnetic-moment.html) of hemoglobin in oxygenated and deoxygenated blood are different.[^2] 
    * Oxygenated hemoglobin is diamagnetic (individual atoms have no magnetic moment hence there is no net magnetic moment).
    * Deoxygenated blood is paramagnetic (atoms have random magnetic moment directions, hence a net magnetic moment).
2. When there is neuronal activity, there is an initial local oxygen consumption which means that deoxyhemoglobin concentration increases locally. This leads to a decrease in BOLD signal called *initial dip* or *fast response*.
3. However, due to the increase in demand for oxygen, an increased blood flow is observed in order to increase the concentration of oxygenated hemoglobin locally.
4. After a few seconds, delivery of oxygenated hemoglobin exceeds the demand which increases local oxygenated hemoglobin concentration significantly ($\approx$ 1 to 3 \% above baseline). This gives rise to a BOLD signal that is much stronger than the initial dip.

Therefore, the BOLD signal can be interpreted as **quantifying regional neuronal activity**.

### Magnetic Resonance and BOLD fMRI
BOLD imaging is the most common method of fMRI.[^3] BOLD MRI is also called fMRI. A couple of useful video resources to get introduced to fMRI are:
* [MRI Physics education materials](https://med.stanford.edu/bmrgroup/education/mri-physics.html), Body MRI Research group, Stanford Medicine
* [MRI Physics](https://www.youtube.com/watch?v=jLnuPKhKXVM), Johns Hopkins Radiology

First of all, fMRI constitutes a large magnet with its own magnetic field $B_0$. Free protons or $H^+$ are the most widely imaged due to the abundance of water in the human body. These $H^+$ ions act like a bar magnet with a positive and a negative pole. 

![magnet](/images/magnet.png)

The orientation of these protons (as a magnet) is in general random but can be influenced by the field $B_0$ associated with the fMRI. The protons align *parallel* or *antiparallel* to the magnetic field $B_0$. However, a small majority of the protons align with the direction of $B_0$. This gives rise to a *net magnetization vector* in the direction of $B_0$. 

![magnets](/images/orient.png) 

In the picture below, the white vector denotes the net magnetization vector in the direction of $B_0$. Using a radiofrequency pulse $B_1$, called *excitation*, we can ``tilt" the net magnetization vector to be perpendicular to $B_0$.

![perp](/images/b0.png) ![perp](/images/b1.png) 

The net magnetization vector will *resonate* or *precess* around the $B_0$ direction. Hence the transverse signal **decays** and the longitudinal signal *recovers*. This recovery is also called *relaxation* while the process of precessing is called relaxation.

![precess](/images/precess.png) ![perp](/images/recover.png) 



[^1]: What is fMRI?, [Oxford Centre for Functional MRI of the Brain](https://www.ndcn.ox.ac.uk/divisions/fmrib/what-is-fmri)
[^2]: Ramani, Ramachandran (ed.), *Functional MRI: Basic Principles and Emerging Clinical Applications for Anesthesiology and the Neurological Sciences*, 1 (New York, 2018; online edn, Oxford Academic, 1 Jan. 2019)
[^3]: Owen J. Arthurs, Simon Boniface, *How well do we understand the neural origins of the fMRI BOLD signal?* - Trends in Neurosciences, Vol 25 Issue 1



