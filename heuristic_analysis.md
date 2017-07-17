# Analysis of planning problems for air cargo traffic system #

## Problem 1 ##

### Optimal plan ###

The optimal solution is clearly to load the cargo in each airport, fly to the other airport, and unload, hence: 

* Load(C1, P1, SFO)
* Load(C2, P2, JFK)
* Fly(P1, SFO, JFK)
* Fly(P2, JFK, SFO)
* Unload(C1, P1, JFK)
* Unload(C2, P2, SFO)

### Non-heuristic search results ###

| Search              | Optimality | Time elapsed | Node expansions |
|--------------------:|-----------:|-------------:|----------------:|
| Breadth-first       |       1.00    |     0.042    |       43        |
| Depth-first         |    0.25    |     0.027    |       33        |
| Uniform cost search |       1.00    |     0.045    |       55        |

Depth-first was the fastest search, but only found a solution of length 24, while breadth-first and uniform cost searches found the optimal solution of length 6, breadth-first slightly more efficiently.

### Heuristic search results ###

|  A star-search heuristic | Optimality | Time elapsed | Node expansions |
|--------------------:|-----------:|-------------:|----------------:|
|       Constant |          1 |         0.04 |              55 |
| Ignore preconditions |          1 |         0.03 |              41 |
|            Level sum |          1 |         0.09 |              39 |

With heuristic search, the optimal solution was found with around the same efficiency in terms of time elapsed and node expansions.

## Problem 2 ##

### Optimal plan ###

The optimal solution is again to load the cargo in each airport, fly to the required airport, and unload, hence: 

* Load(C1, P1, SFO)
* Load(C2, P2, JFK)
* Load(C3, P3, ATL)
* Fly(P1, SFO, JFK)
* Unload(C1, P1, JFK)
* Fly(P2, JFK, SFO)
* Unload(C2, P2, SFO)
* Fly(P3, ATL, SFO)
* Unload(C3, P3, SFO)

### Non-heuristic search results ###

|              Search | Optimality | Time elapsed | Node expansions |
|--------------------:|-----------:|-------------:|----------------:|
|       Breadth-first |          1 |        20.19 |            3343 |
|         Depth-first |      0.015 |         4.94 |             603 |
| Uniform cost search |          1 |        16.16 |            4762 |

Depth-first was most efficient again, but only found a solution of path 599 instead of the optimal 9 as found by both breadth-first and uniform cost searches. This time uniform cost search was fastest, at the cost of more node expansions.

### Heuristic search results ###


|  A star-search heuristic | Optimality | Time elapsed | Node expansions |
|--------------------:|-----------:|-------------:|----------------:|
|             Constant |          1 |        14.76 |            4762 |
| Ignore preconditions |          1 |         4.99 |            1459 |
|            Level sum |          1 |       333.03 |            1129 |

All heuristic searches found the optimal solution faster than both of the optimal non-heuristic searches, with the exception of the level-sum heuristic that took much longer (albeit with fewest node expansions).

## Problem 3 ##

### Optimal plan ###

The optimal solution is now for each plane to load at its original airport, fly to the other airport whose cargo matches the same destination, then fly to the destination to unload its two cargoes. Hence the solution is:

* Load(C1, P1, SFO)
* Load(C2, P2, JFK)
* Fly(P1, SFO, ATL)
* Fly(P2, JFK, ORD)
* Load(C3, P1, ATL)
* Load(C4, P2, ORD)
* Fly(P2, ORD, SFO)
* Fly(P1, ATL, JFK)
* Unload(C1, P1, JFK)
* Unload(C3, P1, JFK)
* Unload(C2, P2, SFO)
* Unload(C4, P2, SFO)

### Non-heuristic search results ###

|              Search | Optimality | Time elapsed | Node expansions |
|--------------------:|-----------:|-------------:|----------------:|
|       Breadth-first |          1 |       151.22 |           14729 |
|         Depth-first |      0.002 |       200.29 |            7202 |
| Uniform cost search |          1 |        62.28 |           17851 |

Yet again, depth-first finds a highly non-optimal solution, with a plan length of 5746 instead of the optimal 12 as found by breadth-first and uniform cost searched. Uniform cost search was around 3 times quicker than breadth-first search.

### Heuristic search results ###

|  A star-search heuristic | Optimality | Time elapsed | Node expansions |
|--------------------:|-----------:|-------------:|----------------:|
|             Constant |          1 |        65.55 |           17851 |
| Ignore preconditions |          1 |        19.43 |            5012 |
|            Level sum |          1 |      1181.74 |            2024 |

Once again, all heuristic searches found the optimal solution, but the level sum heuristic took far longer than the optimal non-heuristic searches, while the "ignore preconditions" heuristic was much faster.

## Conclusion ##

The "ignore preconditions" heuristic was always the fastest planning search, almost always faster than the optimal non-heuristic searches. This could be because despite ignoring the preconditions they still happened to be met much of the time during the search, thereby saving valuable time.
