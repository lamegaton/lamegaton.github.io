---
layout: post
title: Test Markdown and HTML
categories: tech
published: true
---

Jekyll supports the use of [Markdown](http://daringfireball.net/projects/markdown/syntax) with inline HTML tags which makes it easier to quickly write posts with Jekyll, without having to worry too much about text formatting. A sample of the formatting follows.

Tables have also been extended from Markdown:

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

Here's an example of an image, which is included using Markdown:

![Geometric pattern with fading gradient]({{ site.baseurl }}/assets/img/sample_feature_img_2.png)

Highlighting for code in Jekyll is done using Pygments or Rouge. This theme makes use of Rouge by default.

{% highlight js %}
// count to ten
for (var i = 1; i <= 10; i++) {
    console.log(i);
}

// count to twenty
var j = 0;
while (j < 20) {
    j++;
    console.log(j);
}
{% endhighlight %}

Type Theme uses KaTeX to display maths. Equations such as $$ S_n = a \times \frac{1-r^n}{1-r} $$ can be displayed inline.

Alternatively, they can be shown on a new line:

$$ f(x) = \frac{2x^2+4x+6}{x-2} $$
  
$$
  X = 10*\log(\frac{P2}{P1})
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
