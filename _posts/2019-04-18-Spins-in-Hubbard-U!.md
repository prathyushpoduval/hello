---
title: "Spins in Hubbard U!"
date: 2019-04-18T15:34:30-04:00
categories:
  - blog
---


# Setting The Stage
We'll be hunting the Hubbard model to search for Ferromagnetic (FM) and Antiferromagnetic (AFM) phases. The Hubbard hamiltonian is given by

$$H=-t\sum_{\langle ij\rangle}(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}) -\mu \sum_{i\sigma} n_{i\sigma} +U \sum_i n_{i\uparrow}n_{i\downarrow}$$

The first step is to write the interaction term in terms of the Pauli matrices. The Pauli matrices differ from the spin matrices by a factor of $2$. We evaluate

$$\begin{aligned}
\hat{\sigma}^2 &= \hat{\sigma_x}^2+\hat{\sigma_y}^2+\hat{\sigma_z}^2\\
&=(c^{\dagger}_{i\downarrow}c_{i\uparrow}+c^{\dagger}_{i\uparrow}c_{i\downarrow})^2 +i^2(c^{\dagger}_{i\uparrow}c_{i\downarrow}-c^{\dagger}_{i\downarrow}c_{i\uparrow})^2+(c^{\dagger}_{i\downarrow}c_{i\downarrow}-c^{\dagger}_{i\uparrow}c_{i\uparrow})^2\\
&=n_{i\uparrow}+n_{i\downarrow} - 2n_{i\uparrow}n_{i\downarrow}+2n_{i\uparrow}(1-n_{i\downarrow})+2n_{i\downarrow}(1-n_{i\uparrow}) \\
&=3(n_{i\uparrow}+n_{i\downarrow}) - 6n_{i\uparrow}n_{i\downarrow}\end{aligned}$$

Thus, we get that
$n_{i\uparrow}n_{i\downarrow}= -\frac{(\hat{\sigma}\_i)^2}{6} + \frac{1}{2}(n_{i\uparrow}+n_{i\downarrow})$
which gives us 

$$\begin{aligned}
 H &=-t\sum_{\langle ij\rangle}(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}) -\mu \sum_{i\sigma} n_{i\sigma} + \sum_i -\frac{U}{6}(\hat{\sigma}_i)^2+ \sum_i\frac{U}{2}(n_{i\uparrow}+n_{i\downarrow})\\
&=-t\sum_{\langle ij\rangle}(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}) -\mu' \sum_{i\sigma} n_{i\sigma} + \sum_i -\frac{U}{6}(\hat{\sigma}_i)^2 \\
&= \sum_{\sigma}(\epsilon_k-\mu)c^{\dagger}_{k\sigma}c_{k\sigma}-\sum_i \frac{U}{6}(\hat{\sigma}_i)^2\end{aligned}$$

Where we've defined $\mu'=\mu-U/2$ and $\epsilon_k = -2t(\cos{k_x}+\cos{k_y}+\cos{k_z})$. We'll also be setting the lattice constant $a=1$ so that the Broullion zone is $\vec{k}\in [0,2\pi]^3$. We shall redefine $\mu \to \mu'$. Going to the Path integral representation, we get that 

$$\begin{aligned}
    \mathcal{Z}&= \oint \mathcal{D}(\psi) e^{-S}\\
    S&= \int d\tau\left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\frac{U}{6}\sum_i (\sigma_i)^2 \right)\end{aligned}$$
  
Let us redefine $U/3 \to U$. Then, let's introduce the H-S field $\vec{M}_i$ to get 

$$\begin{aligned}
    S&=\int d\tau \left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\frac{U}{2}\sum_i(\sigma_i)^2 +\sum_i \frac{\vec{M_i}^2}{2U}  \right)\end{aligned}$$
    
Then, make the substitution $\vec{M_i} \to \vec{M_i}-U\vec{\sigma_i}$ to get

$$\begin{aligned}
    S&=\int d\tau \left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\sum_i\sigma_i\cdot \vec{M_i} +\sum_i \frac{\vec{M_i}^2}{2U}  \right)\end{aligned}$$
    
Now, we shift to Matsubara - Fourier space. This procedure is a bit
delicate because $\sigma\cdot \vec{M} = {(\sigma_r)}\_{\alpha\beta}M_{r} c^{\dagger}\_{\alpha}c_{\beta}$ (Sum over repeated indices). As a result we can't directly take the Fourier transform of $\sigma$ which is why we did the Hubbard Stratanovich in spatial coordinates. Now, doing the Fourier transform gives

$$\begin{aligned}
    S&=\left(\sum_{kk'\alpha\beta nn'} \bar{\psi}_{k\alpha}(i\omega_n) \left((-i\omega_n + \epsilon_k-\mu)\delta_{kk'}\delta_{nn'} \delta_{\alpha\beta} - \sigma_{\alpha\beta}\cdot\vec{M}_{k-k',n-n'}\right)\psi_{k'\beta}(i\omega_{n'}) \right)  +\beta N\sum_{kn}\frac{M_{k,n}^2}{2U}\end{aligned}$$
    
Where we've defined $M_{k,n} =\frac{1}{\beta N} \int d\tau\sum_r M_i(\tau)e^{-ik\cdot r -i\omega_n\tau}$ and $N$ is the total number of lattice sites in our system. The stage has been set.

# Mean-Field Solutions 
For the mean field solution, we're looking for three main types of solutions, all constant in time:

-   Ferromagnetic: This can be found by finding the MF solution using
    spatially constant $M$ given by $\vec{M}\_q = M\hat{z}\delta_{q0}$.
    We've broken rotational symmetry here by assuming the HS field to be
    pointing along the $z$ direction.

-   Antiferromagnetic: In this solution, the magnitude of $\vec{M}$
    remains constant. However, the direction of $\vec{M}$ at a site is
    opposite to that at neighbouring sites. This can be modelled using
    the trial field $\vec{M}\_r e^{-iK\cdot r}$, where $K=(\pi,\pi,\pi)$.
    As a result,
    $\vec{M}\_q=\frac{M}{2}\hat{z}(\delta_{qK}+\delta_{-qK})$.

-   Both FM and AFM: Where ferromagnetic order and antiferromagnetic
    order coexist. This can be modelled using
    $\vec{M_r} = (M_0 +M_1e^{iK\cdot r})\hat{z}$

The above three are the main types of solutions we'll be looking for. I've worked out the FM-AFM coexistence mean field equations. After
running some numerical simulations, I've found that the mean field solutions have either $M_1=0$ or $M_0=0$, but both can't simultaneously be non-zero. The numerical solutions also support the fact that the FM-AFM transition (if it exists) is a **first order** phase transition. We will see that such a transition does indeed exist.

Ferromagnetism The green's function for this simplified case is

$$\begin{aligned}
    -G^{-1}&=(-i\omega_n+\epsilon_k-\mu)I_2 -\sigma_zM\end{aligned}$$
    
Integrating out the fermions we find that 

$$\begin{aligned}
    -\beta N\mathcal{F}=-\text{Tr}\ln(-G^{-1}) +N\beta\frac{M^2}{2U}\end{aligned}$$
    
Defining $\alpha_{k\sigma}=\epsilon_k-\mu-\sigma M$, we can find

$$\begin{aligned}
    \text{Tr}\ln(-G^{-1})&=\sum_{n,k,\sigma=\pm 1} \ln(-i\omega_n+\alpha_{k\sigma})e^{i\omega_n0^+}\\
    &=\sum_{k\sigma}\ln(e^{-\beta\alpha}+1)\end{aligned}$$ 
    
The MF equations that determine $M$ is given by 

$$\begin{aligned}
    \frac{\partial\mathcal{F}}{\partial M}&=0\\
    \Longrightarrow 0 &= \frac{1}{\beta N} \sum_{k\sigma} \frac{-\beta(-\sigma)}{e^{-\beta\alpha}+1}e^{-\beta\alpha} - \frac{M}{U}\\
    \frac{M}{U}  &= \sum_{\sigma}\int d\epsilon \rho(\epsilon) f(\epsilon -\mu-\sigma M)\sigma\end{aligned}$$
    
Where $\rho(\epsilon)$ is the density of states for the $3D$ tight binding model without spin and $f(x)$ is the Fermi distribution function. To find the zero temperature phase boundary, we first note that $f(x)=\Theta(-x)$ at $0K$. Then we take $M\to 0$ to get

$$\begin{aligned}
    \frac{M}{U}  &= \sum_{\sigma}\int d\epsilon \rho(\epsilon) f(\epsilon -\mu-\sigma M)\sigma\\
    &= \int d\epsilon \rho(\epsilon) (-\frac{df}{d\epsilon}(\epsilon -\mu))(2M)\\
    &= 2M\rho(\mu)\end{aligned}$$ 
    
Thus, the equation for the zero temperature phase diagram is given by $2U\rho(\mu)=1$. Looking at the roots of the inverse green's function, we find that the energy spectrum is given by $\epsilon_k \pm M$. As a result, the Ferromagnetic phase is **gapless**. Because $\M\to 0$ near the phase boundary, the FM-Paramagnet transition is a **second order** transition.

Anti-Ferromagnetism Here, the order parameter couples Fermions at $q$ with those at $q+K$ ($K=(\pi,\pi,\pi)$). Now,$q+K+K=q$ as it goes across the Bruoilloin zone. As a result, we can write our action as

$$\begin{aligned}
    S&=\sum_{q\in \frac{1}{2}BZ, n}\left(\bar{\psi}_{q\uparrow}\text{ }\bar{\psi}_{q\downarrow}\text{ }\bar{\psi}_{q+K\uparrow}\bar{\psi}_{q+K\downarrow}\right) 
    \begin{pmatrix}
    -G_0^{-1}(q,i\omega_n) \mathds{1}_{2\times 2} & -\sigma_z M \\
     -\sigma_z M & -G_0^{-1}(q+K,i\omega_n)  \mathds{1}_{2\times 2}
    \end{pmatrix}
    \begin{pmatrix}\psi_{q\uparrow} \\ \psi_{q\downarrow}\\\psi_{q+K\uparrow}\\\psi_{q+K\downarrow}\end{pmatrix} +\beta N\frac{M^2}{U}\\
    & = \sum_{q\in \frac{1}{2}BZ, n} \vec{\bar{\psi}} \left(-G^{-1}\right) \vec{\psi} + \beta N\frac{M^2}{U}\end{aligned}$$
    
Where we've defined $-G^{-1}\_0 = -i\omega_n +\epsilon_q - \mu$ and we've written the total coupling in terms of a $4\times 4$ matrix. Also note that we have $\epsilon_{q+K} = -\epsilon_q$. Integrating out the fermions, we get that 

$$\begin{aligned}
    S&= -\ln\det\left(-G^{-1}\right) +\beta N\frac{M^2}{2U}\end{aligned}$$
    
Using the formula for the determinant of a block matrix, we find that

$$\begin{aligned}
    \ln\det\left(-G^{-1}\right)&= \sum_{q\in \frac{1}{2}BZ, n} \ln\det\left( G_0^{-1}(q)G_0^{-1}(q+K) - M^2\sigma_z^2\right)\mathds{1}_{2\times 2}\\
    &=  \sum \ln\left( (i\omega_n+\mu)^2 -\epsilon_k^2 - M^2\right)^2\\
    &= 2\sum\left(\ln\left( -i\omega_n+E_k-\mu\right) +\ln\left( -i\omega_n-E_k-\mu\right)\right)\\
    &= 2\sum_{q\in\frac{1}{2}BZ}\left(\ln\left( e^{-\beta(E_k-\mu)} +1\right) + \ln\left( e^{-\beta(-E_k-\mu)} +1\right) \right)\end{aligned}$$
    
Where we've defined $E_k^2=\epsilon_k^2 +M^2$. This strangely looks similar to the BCS gap equations. Thus, we have that 

$$\begin{aligned}
    -\beta N\mathcal{F}&= -2\sum_{q\in\frac{1}{2}BZ}\left(\ln\left( e^{-\beta(E_k-\mu)} +1\right) + \ln\left( e^{-\beta(-E_k-\mu)} +1\right)\right)+\beta N\frac{M^2}{2U}\end{aligned}$$
    
We find the stationary point with respect to $M$. Note that $\frac{\partial E_k}{\partial M} = \frac{M}{E_k}$. We get

$$\begin{aligned}
    0&= \frac{\partial \mathcal{F}}{\partial M}\\
    0& = \frac{2}{\beta N}\sum_{q\in\frac{1}{2}BZ}\left( \frac{-\beta M}{E_k}\frac{e^{-\beta(E_k-\mu)}}{e^{-\beta(E_k-\mu)}+1}  +  \frac{\beta M}{E_k}\frac{e^{-\beta(-E_k-\mu)}}{e^{-\beta(-E_k-\mu)}+1} \right)-\frac{2M}{2U}\\
    \frac{1}{2U} &= \sum_{\sigma=\pm 1}\int d\epsilon\frac{\rho(\epsilon)}{2}\frac{f(\sigma E_k -\mu)}{E_k}(-\sigma)\end{aligned}$$
    
Where we've used the fact that summing over half the BZ (In this
context) is the same as integrating over half the density of states.
Looking at the roots of the inverse green's function, we find that the
energy spectrum is given by $E_k=\pm\sqrt{\epsilon_k^2+M^2}$. As a
result, the Antiferromagnetic phase is **gapped**. Because $\M\to 0$
near the phase boundary, the AFM-Paramagnet transition is a **second
order** transition.

Numericals The key formula we need is one for the density of states.
This was numerically calculated using the formula
$\rho(\epsilon) = \frac{1}{N}\sum_k\delta(\epsilon(k)-\epsilon)$. For
the delta function, a Guassian distribution with $\sigma=0.1$ was used
which qualitatively preserved most of the properties of the density of
states. The integral was done using a total $N=10^5$ points. The results
are in figure (1). The mean field equations were solved using the
density of states calculated. For the phase boundary, I found solutions
where $M\to 0$. For the Ferromagnetic case, this was calculated
analytically to get $2U\rho(\mu) =1$ as the boundary. For the
Antiferromagnet case, I had to numerically find the boundary by setting
$M\sim 0$ and calculating $U$ as a function of $\mu$. Near
$\epsilon,M\sim 0$, $\frac{\rho(\epsilon)}{E_k} \sim \frac{1}{\epsilon}$
because the density of states is constant near $0$. As a result, at half
filling ($\mu=0$), the integral diverges as $M\to 0$. Due to this, we
get Antiferromagnetism for arbitrarily small $U$ at half filling. The
phase boundary is plotted in figure(2), and as we can see there's a
region of overlap of the FM and AFM phase. Thus there should be an
FM-AFM transition that happens in there. While calculting the phase
transition here, we can argue that the transition happens inside the AFM
zone presently calculated. As a result, the AFM-FM transition occurs due
to the **instabilities in the AFM state**. We'll have to calculate the
fluctuations of the AFM goldstone mode and find the location where it
destroys AFM. Numerically, while calculating the simeltaneous AFM-FM
mean field equations, I found that both FM and AFM cannot coexist. This
would lead to the conclusion that the FM-AFM transition is a **first
order** transition.


