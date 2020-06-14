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

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
