---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Sample Complexity of Species Tree Estimation"
summary: "Precise characterization of sample complexity of a popular species tree reconstruction algorithm - ASTRAL"
authors: []
tags: ["ASTRAL", "Phylogenetics"]
categories: ["Computational Biology"]
date: 2020-06-22T02:10:42-07:00
weight: 50

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
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
url_pdf: "https://arxiv.org/abs/1704.06831"
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---


ASTRAL <span style="color:blue"> (Mirarab et al., 2014)[^mirarab] </span> is a method of reconstructing species trees from a given set of gene trees that have been reconstructed from sequence data. While it was shown to be statistically consistent in <span style="color:blue"> (Mirarab et al., 2014) [^mirarab] </span>, not much was known about its sample complexity, i.e., the number of gene trees ($m$) required to reconstruct the true species tree with high probability. In <span style="color:blue">(Shekhar et al., 2018)[^shekhar2018]</span>, we provided a tight characterization of the data requirement (i.e., $m$) of ASTRAL in terms of the number of leaves ($n$) and the length of the shortest branch ($f$).

More formally, under the [Multispecies Coalescent](https://en.wikipedia.org/wiki/Multispecies_coalescent_process) (MSC) model, for the class of species trees with $n$ leaves and the shortest branch length ($f$) sufficiently small,  we obtained the following results:

* We first showed that $\mathcal{O} \left( f^{-2} \log n \right)$ gene trees are sufficient for ASTRAL to output the true species tree with high probability. This result follows from the standard argument of applying Hoeffding’s inequality followed by a union bound. 
* Proving that $m= \Omega\left ( f^{-2} \log n \right)$ is also necessary was more involved. We proceeded in the following steps: 

    * We began by proving a weaker result. We showed that with $m \leq \mathcal{O} \left (f^{-2}\right)$ gene trees, a quartet species tree is wrongly reconstructed by ASTRAL with probability close to 0.5. For obtaining this result, we reduced the error event to the study the deviation of a binomial random variable and then used the [Berry-Esseen theorem](https://en.wikipedia.org/wiki/Berry%E2%80%93Esseen_theorem) to approximate this binomial. Having obtained the result for the quartet ($n=4$) case, we extended this result to the general case by constructing a species tree consisting of a triplet joined to the rest of the tree by a long branch.  

    * Using the insights from the previous result, we then strengthened it to match the sufficient conditions on $m$. In particular, by allowing an extra  $\log(n)$ factor and using stronger deviation inequalities for binomial random variables, we showed that the error in reconstructing the quartet species tree is at least $1/n^{a}$  for some $a>0$ . Then by considering a tree with $n/3$ triplets joined by long branches, we showed that the reconstruction error can be made arbitrarily close to $1$, for $m \leq (a/5)f^{-2} \log n$. 

These results imply that for ASTRAL to guarantee correct reconstruction with high probability uniformly over the space of all species trees, $\Theta\left(f^{-2}\log n\right)$ gene trees are both necessary and sufficient.

### References

[^mirarab]: Mirarab, S., Reaz, R., Bayzid, M. S., Zimmermann, T., Swenson, M. S., & Warnow, T. (2014). ASTRAL: genome-scale coalescent-based species tree estimation. _Bioinformatics_.

[^shekhar2018]: Shekhar, S., Roch, S., & Mirarab, S. (2017). Species tree estimation using ASTRAL: how many genes are enough?. _IEEE/ACM transactions on computational biology and bioinformatics_.







