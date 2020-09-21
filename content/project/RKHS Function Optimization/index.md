---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Kernelized Bandits"
summary: "Algorithm with uniformly improved regret bounds + a computationally efficient heuristic with better empirical performance
 "
authors: []
tags: ["RKHS", "Holder Spaces", "Hyperparameter Tuning"]
categories: ["Bandits", "Optimization"]
date: 2020-06-22T02:08:26-07:00
weight: 30

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: "Performance of LP-GP-UCB~(L) and Heuristic~(H) algorithms along with some baselines (IGPUCB~(I), GP-EI~(E), GP-PI~(P)) on 8 dimensional Branin function"
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
# links:
# - name: Follow
#   url: https://twitter.com
#   icon_pack: fab
#   icon: twitter

url_code: ""
url_pdf: "https://arxiv.org/abs/2005.04832"
url_slides: "slides.pdf"
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---

Kernelized bandits refers to a non-Bayesian formulation of the problem of optimizing a black-box function $f$ which can only be accessed through a noisy zero-order oracle. Here, instead of assuming that $f$ is a sample from a Gaussian Process (GP), we assume that the function $f$ has bounded norm in the RKHS associated with the positive-definite kernel $K$. Existing algorithms in this area admit an upper bound on the cumulative regret of the form $$ \mathcal{R}\_n = \tilde{\mathcal{O}}\left( \gamma\_n \sqrt{n} \right)$$ where $\gamma\_n = \max\_{S} I(y\_S; f)$ is the _maximum information gain_ associated with kernel $K$, where the maximum is over subsets $S$ of cardinality $n$. 

Recent work by <span style="color:blue">(Scarlett et al., 2017)[^scarlett]</span> demonstrated a large gap in the existing upper bounds on $\mathcal{R}\_n$ and algorithm-independent lower bounds for am important family of kernels. Our work[^shekhar] seeks to address this issue by proposing an novel algorithm for kernelized bandits with uniformly tighter regret bounds.

>The key idea of our work is to augment the global GP surrogate with Local Polynomial (LP) estimators on the elements of an adaptively constructed partition, $\mathcal{P}_t$ of the input space $\mathcal{X}$.

This idea, combined with an embedding result, which imples that the elements of the RKHS associated with the Matern family of kernels can be embedded into certain Holder spaces, allows us to derive uniformly better regret bounds.

---

Our main contributions are:

* We first propose an algorithm, called LP-GP-UCB, which uses LP estimators along with the global GP surrogate to construct tighter UCB for $f$ to guide the query strategy.

* Under assumptions that $f$ has finite norm in RKHS and in a Holder space, we obtain general regret bounds for our proposed algorithm.

* For commonly used kernels, we then obtain embedding results which show that for these kernels the Holder assumption follows from the bounded RKHS norm assumption. This allows us to specialize the general regret bounds for several important kernel families such as Squared Exponential, Matern, Rational-Quadratic and Gamma-Exponential kernels.

* Next, we propose a computationally efficient heuristic, which employs standard regression trees to construct the non-uniform partition of the input space. Experiments with benchmark functions as well as a hyperparameter tuning task demonstrate the benefits of our proposed approach.

For more details please refer to the overview slides [here](./slides.pdf) and the preprint [here](https://arxiv.org/abs/2005.04832).


### References

[^scarlett]: Scarlett, J., Bogunovic, I., & Cevher, V. (2017). Lower bounds on regret for noisy gaussian process bandit optimization. _COLT_.

[^shekhar]: Shekhar, S., & Javidi, T. (2020). Multi-scale Zero Order Optimization of Smooth Functions in an RKHS. _preprint_

















