---
title: "Magnetism in Hubbard Model"
date: 2020-06-14T15:34:30-04:00
categories:
  - blog
tags:
  - Hubbard
  - Magnetism
  -Spin
---

#Setting The Stage#

We'll be hunting the Hubbard model to search for Ferromagnetic (FM) and Antiferromagnetic (AFM) phases. The Hubbard hamiltonian is given by 
$$H=-t\sum_{\langle ij\rangle}(\cd{i}\cc{j}+\cd{j}\cc{i}) -\mu \sum_{i\sigma} n_{i\sigma} +U \sum_i n_{i\uparrow}n_{i\downarrow}  $$
The first step is to write the interaction term in terms of the Pauli matrices. The Pauli matrices differ from the spin matrices by a factor of $2$. We evaluate
$$
\begin{align*}
\hat{\sigma}^2 &= \hat{\sigma_x}^2+\hat{\sigma_y}^2+\hat{\sigma_z}^2\\
&=(\cdU{i}\cD{i}+\cdD{i}\cU{i})^2 +i^2(\cdD{i}\cU{i}-\cdU{i}\cD{i})^2+(\cdU{i}\cU{i}-\cdD{i}\cD{i})^2\\
&=n_{i\uparrow}+n_{i\downarrow} - 2n_{i\uparrow}n_{i\downarrow}+2n_{i\uparrow}(1-n_{i\downarrow})+2n_{i\downarrow}(1-n_{i\uparrow}) \\
&=3(n_{i\uparrow}+n_{i\downarrow}) - 6n_{i\uparrow}n_{i\downarrow}
\end{align*}
$$
Thus, we get that $n_{i\uparrow}n_{i\downarrow}= -\frac{(\hat{\sigma}_i)^2}{6} + \frac{1}{2}(n_{i\uparrow}+n_{i\downarrow})$ which gives us 
$$
\begin{align*}
 H &=-t\sum_{\langle ij\rangle}(\cd{i}\cc{j}+\cd{j}\cc{i}) -\mu \sum_{i\sigma} n_{i\sigma} + \sum_i -\frac{U}{6}(\hat{\sigma}_i)^2+ \sum_i\frac{U}{2}(n_{i\uparrow}+n_{i\downarrow})\\
&=-t\sum_{\langle ij\rangle}(\cd{i}\cc{j}+\cd{j}\cc{i}) -\mu' \sum_{i\sigma} n_{i\sigma} + \sum_i -\frac{U}{6}(\hat{\sigma}_i)^2 \\
&= \sum_{\sigma}(\epsilon_k-\mu)\cd{k}\cc{k}-\sum_i \frac{U}{6}(\hat{\sigma}_i)^2
\end{align*}
$$
Where we've defined $\mu'=\mu-U/2$ and $\epsilon_k = -2t(\cos{k_x}+\cos{k_y}+\cos{k_z})$. We'll also be setting the lattice constant $a=1$ so that the Broullion zone is $\vec{k}\in [0,2\pi]^3$. We shall redefine $\mu \to \mu'$. Going to the Path integral representation, we get that 
$$
\begin{align*}
    \mathcal{Z}&= \oint \mathcal{D}(\psi) e^{-S}\\
    S&= \int d\tau\left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\frac{U}{6}\sum_i (\sigma_i)^2 \right)
\end{align*}
$$
Let us redefine $U/3 \to U$. Then, let's introduce the H-S field $\vec{M}_i$ to get
$$
\begin{align*}
    S&=\int d\tau \left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\frac{U}{2}\sum_i(\sigma_i)^2 +\sum_i \frac{\vec{M_i}^2}{2U}  \right)
\end{align*}
$$
Then, make the substitution $\vec{M_i} \to \vec{M_i}-U\vec{\sigma_i}$ to get 
$$
\begin{align*}
    S&=\int d\tau \left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\sum_i\sigma_i\cdot \vec{M_i} +\sum_i \frac{\vec{M_i}^2}{2U}  \right)
\end{align*}
$$
Now, we shift to Matsubara - Fourier space. This procedure is a bit delicate because $\sigma\cdot \vec{M} = (\sigma_r)_{\alpha\beta} M_r c^{\dagger}_{\alpha}c_{\beta}$ (Sum over repeated indices). As a result we can't directly take the Fourier transform of $\sigma$ which is why we did the Hubbard Stratanovich in spatial coordinates. Now, doing the Fourier transform gives
$$
\begin{align*}
    S&=\left(\sum_{kk'\alpha\beta nn'} \bar{\psi}_{k\alpha}(i\omega_n) \left((-i\omega_n + \epsilon_k-\mu)\delta_{kk'}\delta_{nn'} \delta_{\alpha\beta} - \sigma_{\alpha\beta}\cdot\vec{M}_{k-k',n-n'}\right)\psi_{k'\beta}(i\omega_{n'}) \right)  +\beta N\sum_{kn}\frac{M_{k,n}^2}{2U}
\end{align*}
$$
Where we've defined $M_{k,n} =\frac{1}{\beta N} \int d\tau\sum_r M_i(\tau)e^{-ik\cdot r -i\omega_n\tau}$ and $N$ is the total number of lattice sites in our system. The stage has been set.
