# Edmonds's blossom algorithm for maximum weight matching in undirected graphs

This library implements the Blossom algorithm that computes a maximum weighted matching of an undirected graph in O(number of nodes ** 3).

It was ported from the python code authored by Joris van Rantwijk included in the NetworkX graph library and modified.

## Getting started

Add the necessary dependencies to your project:

```clojure
[ageneau/blossom "0.1.0"]
[aysylu/loom "1.0.2"]
```

## Usage

[//]: # (FIXME: update) 

```clojure
(ns test.blossom
  (:require [blossom.max-weight-matching :as mwm]
            [loom.graph :as graph]))

(def g (-> (graph/weighted-graph)
                (graph/add-edges [1 2 2][1 3 -2][2 3 1]
                                 [2 4 -1][3 4 -6])))

;; Compute a maximum weigted matching
(def maxw-matching (b/max-weight-matching g))
;; => #{#{1 2}}

;; Compute the maximum-cardinality matching with maximum weight among all
;; maximum-cardinality matchings.
(def maxc-matching (b/max-weight-matching g {:max-cardinality true}))
;; => #{#{4 2} #{1 3}}

;; Compute a maximal matching (not necessarily max weight)
(def max-matching (b/maximal-matching g))
;; => #{#{4 3} #{1 2}}

(b/is-matching? g maxw-matching)
;; => true

(b/is-maximal-matching? g maxw-matching)
;; => false

(b/is-maximal-matching? g maxc-matching)
;; => true

(b/is-maximal-matching? g max-matching)
;; => true


```

## License

Copyright &copy; NetworkX developers.
Copyright (C) 2004-2018 by
    Aric Hagberg <hagberg@lanl.gov>
    Dan Schult <dschult@colgate.edu>
    Pieter Swart <swart@lanl.gov>

Copyright &copy; 2008 by
    Joris van Rantwijk.

Copyright &copy; 2011 by
    Nicholas Mancuso <nick.mancuso@gmail.com>

Copyright &copy; 2018 Sylvain Ageneau

All rights reserved.

This project is licensed under the [BSD 3-Clause "New" or "Revised" License][license].

[license]: https://opensource.org/licenses/BSD-3-Clause
