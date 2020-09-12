---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Bayesian Optimization"
summary: "Low complexity algorithms with improved regret bounds"
authors: []
tags: ["Bayesian Optimization", "GP Bandits", "Hyperparameter Tuning"]
categories: ["Optimization", "Bandits"]
date: 2020-06-22T02:02:52-07:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "black-box function optimization"
  focal_point: ""
  preview_only: true

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: "https://projecteuclid.org/euclid.ejs/1543892564"
url_slides: "Slides.pdf"
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---



Several applications, such as hyperparameter tuning, can be formulated as the problem 
of optimizing a noisy black-box function ($f$) that is expensive to evaluate. In the field of [Bayesian Optimization](https://distill.pub/2020/bayesian-optimization/) (also referred to as _Gaussian Process Bandits_), the process of optimization is driven by utilizing a [Gaussian Process]() surrogate model to guide the search for optimum. 

Under the assumption that the unknown function $f$ is a sample from a zero mean Gaussian Process (GP) with known covariance function $K$, and given a sampling budget $n$, the goal of the agent is to design a sequential strategy to query 
the black-box function (noisy zeroth order oracle), in order to learn about its 
maximizer. The performance of an algorithm is measured  by its __cumulative regret__ $\mathcal{R}\_n$, 
defined as $\mathcal{R}\_n=\sum_{t=1}^n f(x^\*) - f(x\_t)$. 

Existing results in literature have obtained 
regret bounds of the form $\mathcal{R}\_n = \mathcal{O} \left ( \sqrt{n \log n \gamma\_n}\right)$, where $\gamma\_n$ is the 
maximum information that can be gained about $f$ from $n$ samples. 


### [Improved Bounds for  Bayesian GP Bandits](https://projecteuclid.org/euclid.ejs/1543892564). 

Our work in this area was motivated by the following informal idea: 
> Since our goal is to learn about a maximizer of $f$, and not necessarily about the whole function, can we identify cases in which the $\gamma_n$ based bounds are loose.

 Our main contributions were: 

* Following the above intuition, we first constructed two Gaussian Processes for which we showed that the $\gamma\_n$ based bounds were very loose. 

* Next, we proposed an algorithm which constructs a non-uniform partition of the input space and focuses sampling in the near optimal regions. For this algorithm we obtained bounds on $\mathcal{R}_n$ which were tighter than the existing results. In particular, we obtained the __first sublinear regret bounds__ for the exponential kernel, and __strictly better regret bounds for Matern kernels__ when $D>\nu-1$, where $D$ is the dimension of the input space, and $\nu$ is the smoothness parameter of the Matern kernel. 

* We then extended our algorithm to the case of Contextual GP bandits, and obtained improvements over the results of <span style="color:blue">(Krause and Ong, 2011)[^krause2011]</span>. 

* Finally, we also showed that the techniques developed can also be used to propose a Bayesian version of the Zooming algorithm of <span style="color:blue"> (Kleinberg et al., 2008)[^klein2008]</span>. 


### [Extension to GP Level Set Estimation](http://proceedings.mlr.press/v89/shekhar19a.html) 

In some problems the goal is not to learn about the optimizer of $f$, but instead to 
estimate the $\lambda$-level set of the function, i.e., the region of the input space where $f$ is above a threshold $\lambda$. In <span style="color:blue">(Shekhar and Javidi, 2019)[^shekhar1]</span> , we extended the techniques developed in <span style="color:blue">(Shekhar and Javidi, 2018) [^shekhar2]</span> to propose a GP level set estimation algorithm with __improved convergence rates__ and __lower computational complexity__ than the previous known results of <span style="color:blue"> Gotovos et al., 2013 [^gotovos2013]</span>. In addition, by exploiting the structured nature of the evaluation points of our proposed algorithm, we also obtained __tighter bounds on the information gain__ of our algorithm.


### References

[^krause2011]: Krause, A., & Ong, C. S. (2011). Contextual gaussian process bandit optimization. _Neurips_

[^klein2008]: Kleinberg, R., Slivkins, A., & Upfal, E. (2008). Multi-armed bandits in metric spaces. _STOC_

[^shekhar1]: Shekhar, S., & Javidi, T. (2019). Multi-Scale Gaussian Process Level Set Estimation. _AISTATS_.

[^shekhar2]: Shekhar, S., & Javidi, T. (2018). Gaussian Process Bandits with Adaptive Discretization. _Electronic Journal of Statistics_.


[^gotovos2013]: Gotovos, A., Casati, N., Hitz, G., & Krause, A. (2013). Active learning for level set estimation. _IJCAI_.

