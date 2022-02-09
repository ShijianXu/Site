---
author: "DarthXSJ"
date: 2019-05-23
title: Setting MathJax
best: False
---

To write math expressions in Hugo, a popular method is using [MathJax](https://www.mathjax.org/). This [blog](https://divadnojnarg.github.io/blog/mathjax/) gives a quick and simple solution. 

First, write a script. I will copy the script as follow:

```
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.1/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
  MathJax.Hub.Config({
  tex2jax: {
    inlineMath: [['$','$'], ['\\(','\\)']],
    displayMath: [['$$','$$'], ['\[','\]']],
    processEscapes: true,
    processEnvironments: true,
    skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
    TeX: { equationNumbers: { autoNumber: "AMS" },
         extensions: ["AMSmath.js", "AMSsymbols.js"] }
  }
  });
  MathJax.Hub.Queue(function() {
    // Fix <code> tags after MathJax finishes running. This is a
    // hack to overcome a shortcoming of Markdown. Discussion at
    // https://github.com/mojombo/jekyll/issues/199
    var all = MathJax.Hub.getAllJax(), i;
    for(i = 0; i < all.length; i += 1) {
        all[i].SourceElement().parentNode.className += ' has-jax';
    }
  });

  MathJax.Hub.Config({
  // Autonumbering by mathjax
  TeX: { equationNumbers: { autoNumber: "AMS" } }
  });
</script>
```

What to do next is naming this script like **mathjax_support.html** and saving it in the */layout/partials* folder. Then add a line in **header.html**, like this:

```
{{ partial "mathjax_support.html" . }}
```

It's done! Here are some tests.

```
AveP = \int_0^1 p\(r\) dr
```

$$
AveP = \int_0^1 p\(r\) dr
$$

```
\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi \\\\\\ 1+2 \\\\\\ a\_6
```

$$
\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi \\\\\\ 1+2 \\\\\\ a\_6
$$

```
\require{cancel}\begin{array}{rl}
\verb|y+\cancel{x}| & y+\cancel{x} \newline
\verb|\cancel{y+x}| & \cancel{y+x} \newline
\verb|y+\bcancel{x}| & y+\bcancel{x} \newline
\verb|y+\xcancel{x}| & y+\xcancel{x} \newline
\verb|y+\cancelto{0}{x}| & y+\cancelto{0}{x} \newline
\verb+\frac{1\cancel9}{\cancel95} = \frac15+& \frac{1\cancel9}{\cancel95} = \frac15 \\
\end{array}
```

$$
\require{cancel}\begin{array}{rl}
\verb|y+\cancel{x}| & y+\cancel{x} \newline
\verb|\cancel{y+x}| & \cancel{y+x} \newline
\verb|y+\bcancel{x}| & y+\bcancel{x} \newline
\verb|y+\xcancel{x}| & y+\xcancel{x} \newline
\verb|y+\cancelto{0}{x}| & y+\cancelto{0}{x} \newline
\verb+\frac{1\cancel9}{\cancel95} = \frac15+& \frac{1\cancel9}{\cancel95} = \frac15 \\
\end{array}
$$

```
f(n)= \begin{cases} n/2, & \text {if $n$ is even} \newline 3n+1, & \text{if $n$ is odd} \end{cases}
```

$$ f(n)= \begin{cases} n/2, & \text {if $n$ is even} \newline 3n+1, & \text{if $n$ is odd} \end{cases} $$

```
\begin{cases}
\dot{x} & = \sigma(y-x) \newline
\dot{y} & = \rho x - y - xz \newline
\dot{z} & = -\beta z + xy
\end{cases}
```

$$
\begin{cases}
\dot{x} & = \sigma(y-x) \newline
\dot{y} & = \rho x - y - xz \newline
\dot{z} & = -\beta z + xy
\end{cases}
$$


