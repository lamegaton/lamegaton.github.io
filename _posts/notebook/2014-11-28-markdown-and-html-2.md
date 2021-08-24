---
layout: post
title: Test Markdown and HTML 2
categories: tech
published: true
comments: false
---
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.13.13/dist/katex.min.css" integrity="sha384-RZU/ijkSsFbcmivfdRBQDtwuwVqK7GMOw6IMvKyeWL2K5UAlyp6WonmB8m7Jd0Hn" crossorigin="anonymous">
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.13.13/dist/katex.min.js" integrity="sha384-pK1WpvzWVBQiP0/GjnvRxV4mOb0oxFuyRxJlk6vVw146n3egcN5C925NCP7a7BY8" crossorigin="anonymous"></script>
<script defer src="https://cdn.jsdelivr.net/npm/katex@0.13.13/dist/contrib/auto-render.min.js" integrity="sha384-vZTG03m+2yp6N6BNi5iM4rW4oIwk5DfcNdFfxkk9ZWpDriOkXX8voJBFrAO7MpVl" crossorigin="anonymous"
    onload="renderMathInElement(document.body);"></script>



Type Theme uses KaTeX to display maths. Equations such as $$ S_n = a \times \frac{1-r^n}{1-r} $$ can be displayed inline.

Alternatively, they can be shown on a new line:

$$ f(x) = \frac{2x^2+4x+6}{x-2} $$
  
$$
  X = 10 \log(\frac{P2}{P1})
$$

Type math within a sentence $$2x^2 + x + c$$ to display inline  

$$
  \bar{y} = {1 \over n} \sum_{i = 1}^{n}y_i
$$

\\[ \frac{1}{n^{2}} \\]

 {% raw %}
  $$a^2 + b^2 = c^2$$ --> note that all equations between these tags will not need escaping! 
 {% endraw %}


Type Theme uses KaTeX to display maths. Equations such as $$S_n = a \times \frac{1-r^n}{1-r}$$ can be displayed inline.

Alternatively, they can be shown on a new line:

$$ f(x) = \int \frac{2x^2+4x+6}{x-2} $$

$$\LaTeX code$$   (for display)  
\\[\LaTeX code\\] (also for display)  
\\(\LaTeX code\\) (for inline)  