---
title: "The Value of Excess Supply in Spatial Matching Markets"
collection: publications
permalink: /publication/2021-pricing-vs-matching
excerpt: 'We show that in a dynamic spatial matching market, no level of sophistication in the matching algorithm and no amount of data to predict times and locations of future demand can beat a naive greedy algorithm with a small excess supply.'
date: 2021-07-01
venue: 'with Mohammad Akbarpour, Shengwu Li and Amin Saberi (Work in Progress)'
paperurl: 'https://yalimohammadi.github.io/files/arxivSpatialMarkets.pdf'
---
We study dynamic matching in a spatial setting: there are $n$ riders and $m$ drivers placed uniformly at random on the interval $[0,\ell]$.   The location of the drivers is known. The riders arrive in some (possibly adversarial) order and they have to be matched irrevocably to a driver at the time of  arrival. The cost of matching a driver to a rider is equal to the $l_1$-norm of their distance on the interval. The question we consider is  which strategy is better: to boost supply by attracting more drivers to the platform, or to have a perfect forecast and design an optimal matching technology?

We prove that if  $m\geq (1+\epsilon)n$ for some $\epsilon>0$, the cost of matching returned by a simple greedy algorithm which pairs each arriving rider to the closest available driver is $\tilde{O}(\ell)$. On the other hand, when $n=m$, even an omniscient algorithm with perfect knowledge about the positions of riders cannot find a matching with cost better than $\Theta(\ell\sqrt{n})$. Our results shed light on the important role of supply in spatial matching markets: No level of sophistication in the matching algorithm and no amount of data to predict times and locations of future demand can beat a myopic greedy algorithm with a small excess supply.
