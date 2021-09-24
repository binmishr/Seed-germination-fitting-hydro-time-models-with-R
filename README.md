# Seed-germination-fitting-hydro-time-models-with-R

The details of the codeset and plots are included in the attached Adobe Acrobat reader (.pdf) file in this repository. 
You need to download the same to view the contents. There are referrals to other contents in BLUE colour also to follow.

A Brief Introduction
======================

I am locked at home, due to the COVID-19 emergency. Luckily I am healthy, but there is not much to do, inside. I thought it might be nice to spend some time to talk about seed germination models and the connections with survival analysis.

We all know that seeds need water to germinate. Indeed, the absorption of water activates the hydrolytic enzymes, which break down food resources stored in seeds and provide energy for germination. As the consequence, there is a very close relationship between water content in the substrate and germination velocity: the higher the water content the quickest the germination, as long as the availability of oxygen does not become a problem (well, water and oxygen in soil may compete for space and a high water content may result in oxygen shortage).

Indeed, it is relevant to build germination models, linking the proportion of germinated seeds to water availability in the substrate; these models are usually known as hydro-time (HT) models. The starting point is the famous equation of Bradford (1992), where the germination rate (GR) for the \(i-th\) seed in the lot is expressed as a linear function of water potential in the substrate (\(\Psi\)):

\[ GR_i = \textrm{min} \left( \frac{\Psi – \Psi_{b(i)}}{\theta_H}; 0 \right) \quad \quad \quad \quad (1)\]

In that equation, \(\Psi_{b(i)}\) is the base water potential for the \(i-th\) seed and \(\theta_H\) is the hydro-time constant, expressed as MPa day or MPa hour. The concept is relatively simple: we just need to remember that the water can only move from a position with a higher water potential to a position with a lower water potential. Therefore, a seed cannot germinate when its base water potential is higher than the water potential in the substrate.

When \(\Psi > \Psi_b(i)\), the germination rate of the \(i-th\) seed is linearly related to \(\Psi\): the higher this latter value, the higher the germination rate. Now we should consider that the germination rate is the inverse of the germination time (\(GR = 1/t\)); thus, the higher the GR, the shortest the germination time. Germination is achieved at the time \(t\) when:

\[ t \, \left( \Psi – \Psi_{b(i)} \right) = \theta_H \quad \quad \quad (2)\]

Elsewhere in this website, I show that Equation 1 can be fitted to germination data in a two-steps fashion. In this page we will see how we can embed Equation 1 into a germination model, to predict the proportion of germinated seeds, depending on time and water content in the substrate. As usual, let’s start from a practical example.
