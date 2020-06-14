---
title: "Welcome to Jekyll!"
date: 2019-04-18T15:34:30-04:00
categories:
  - blog
tags:
  - Jekyll
  - update
---

You'll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated. Upd 5

$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

Jekyll also offers powerful support for code snippets:

```ruby
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
```
`\ifdim\@tempskipa <\z@ \@tempskipa -\@tempskipa \@afterindentfalse\fi`{=latex}
Setting The Stage [\[sec:background\]]{#sec:background
label="sec:background"} We'll be hunting the Hubbard model to search for
Ferromagnetic (FM) and Antiferromagnetic (AFM) phases. The Hubbard
hamiltonian is given by
$$H=-t\sum_{\langle ij\rangle}(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}) -\mu \sum_{i\sigma} n_{i\sigma} +U \sum_i n_{i\uparrow}n_{i\downarrow}$$
The first step is to write the interaction term in terms of the Pauli
matrices. The Pauli matrices differ from the spin matrices by a factor
of $2$. We evaluate $$\begin{aligned}
\hat{\sigma}^2 &= \hat{\sigma_x}^2+\hat{\sigma_y}^2+\hat{\sigma_z}^2\\
&=(c^{\dagger}_{i\downarrow}c_{i\uparrow}+c^{\dagger}_{i\uparrow}c_{i\downarrow})^2 +i^2(c^{\dagger}_{i\uparrow}c_{i\downarrow}-c^{\dagger}_{i\downarrow}c_{i\uparrow})^2+(c^{\dagger}_{i\downarrow}c_{i\downarrow}-c^{\dagger}_{i\uparrow}c_{i\uparrow})^2\\
&=n_{i\uparrow}+n_{i\downarrow} - 2n_{i\uparrow}n_{i\downarrow}+2n_{i\uparrow}(1-n_{i\downarrow})+2n_{i\downarrow}(1-n_{i\uparrow}) \\
&=3(n_{i\uparrow}+n_{i\downarrow}) - 6n_{i\uparrow}n_{i\downarrow}\end{aligned}$$
Thus, we get that
$n_{i\uparrow}n_{i\downarrow}= -\frac{(\hat{\sigma}\_i)^2}{6} + \frac{1}{2}(n_{i\uparrow}+n_{i\downarrow})$
which gives us $$\begin{aligned}
 H &=-t\sum_{\langle ij\rangle}(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}) -\mu \sum_{i\sigma} n_{i\sigma} + \sum_i -\frac{U}{6}(\hat{\sigma}_i)^2+ \sum_i\frac{U}{2}(n_{i\uparrow}+n_{i\downarrow})\\
&=-t\sum_{\langle ij\rangle}(c^{\dagger}_{i\sigma}c_{j\sigma}+c^{\dagger}_{j\sigma}c_{i\sigma}) -\mu' \sum_{i\sigma} n_{i\sigma} + \sum_i -\frac{U}{6}(\hat{\sigma}_i)^2 \\
&= \sum_{\sigma}(\epsilon_k-\mu)c^{\dagger}_{k\sigma}c_{k\sigma}-\sum_i \frac{U}{6}(\hat{\sigma}_i)^2\end{aligned}$$
Where we've defined $\mu'=\mu-U/2$ and
$\epsilon_k = -2t(\cos{k_x}+\cos{k_y}+\cos{k_z})$. We'll also be setting
the lattice constant $a=1$ so that the Broullion zone is
$\vec{k}\in [0,2\pi]^3$. We shall redefine $\mu \to \mu'$. Going to the
Path integral representation, we get that $$\begin{aligned}
    \mathcal{Z}&= \oint \mathcal{D}(\psi) e^{-S}\\
    S&= \int d\tau\left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\frac{U}{6}\sum_i (\sigma_i)^2 \right)\end{aligned}$$
Let us redefine $U/3 \to U$. Then, let's introduce the H-S field
$\vec{M}_i$ to get $$\begin{aligned}
    S&=\int d\tau \left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\frac{U}{2}\sum_i(\sigma_i)^2 +\sum_i \frac{\vec{M_i}^2}{2U}  \right)\end{aligned}$$
Then, make the substitution $\vec{M_i} \to \vec{M_i}-U\vec{\sigma_i}$ to
get

$$\begin{aligned}
    S&=\int d\tau \left(\sum_{k\sigma} \bar{\psi}_{k\sigma} (\partial_{\tau} + \epsilon_k-\mu)\psi_{k\sigma}-\sum_i\sigma_i\cdot \vec{M_i} +\sum_i \frac{\vec{M_i}^2}{2U}  \right)\end{aligned}$$
Now, we shift to Matsubara - Fourier space. This procedure is a bit
delicate because
$\sigma\cdot \vec{M} = (\sigma_r)_{\alpha\beta} M_r c^{\dagger}_{\alpha}c_{\beta}$
(Sum over repeated indices). As a result we can't directly take the
Fourier transform of $\sigma$ which is why we did the Hubbard
Stratanovich in spatial coordinates. Now, doing the Fourier transform
gives

$$\begin{aligned}
    S&=\left(\sum_{kk'\alpha\beta nn'} \bar{\psi}_{k\alpha}(i\omega_n) \left((-i\omega_n + \epsilon_k-\mu)\delta_{kk'}\delta_{nn'} \delta_{\alpha\beta} - \sigma_{\alpha\beta}\cdot\vec{M}_{k-k',n-n'}\right)\psi_{k'\beta}(i\omega_{n'}) \right)  +\beta N\sum_{kn}\frac{M_{k,n}^2}{2U}\end{aligned}$$
Where we've defined
$M_{k,n} =\frac{1}{\beta N} \int d\tau\sum_r M_i(\tau)e^{-ik\cdot r -i\omega_n\tau}$
and $N$ is the total number of lattice sites in our system. The stage
has been set.

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
