## LAP-JV
### Linear Assignment Problem — algorithm by R. Jonker and A. Volgenant

“A shortest augmenting path algorithm for dense and sparse linear assignment problems,” by R. Jonker and A. Volgenant, _Computing_ (1987) 38: 325. doi:10.1007/BF02278710
 
Ported to javascript by Philippe Rivière, from the C++ implementation found at https://github.com/yongyanghz/LAPJV-algorithm-c

Added an epsilon to avoid infinite loops caused by rounding errors.


## Usage

In the [Linear Assignment Problem](https://en.wikipedia.org/wiki/Assignment_problem), you have _n_ agents and _n_ tasks, and need to assign one task to each agent, at minimal cost.

First, compute the cost matrix: how expensive it is to assign agent _i_ (rows) to task _j_ (columns).

The LAP-JV algorithm will give an optimal solution:

```javascript
  n = 3, costs = [[1,2,3], [4,2,1], [2,2,2]];
  //               ^ _ _    _ _ ^    _ ^ _
  solution = lap(n, costs);

  console.log(solution.col);
  // [0, 2, 1]
  console.log(solution.cost);
  // 4
```

Here agent 0 is assigned to task 0, agent 1 to task 2, agent 2 to task 1, resulting in a total cost of `1 + 1 + 2 = 4`.


**Cost callback**

For performance and usability reasons, the `lap` function now accepts a cost callback `cost(i,j)` instead of a cost matrix:
```javascript
   var pos = new Float32Array(1000).map(d => Math.random());
   lap(pos.length, (i,j) => (pos[i]*10 - j) * (pos[i]*10 - j));
```

## 

The algorithm runs in `O(n^2)`. You can run it [directly](http://bl.ocks.org/Fil/6ead5eea43ec506d5550f095edc45e3f) or as a javascript worker, as in the following example:

[![](https://gist.githubusercontent.com/Fil/d9752d8c41cc2cc176096ce475233966/raw/88c1e7e4d62df8145a68808b7252cd5013e0394f/thumbnail.png)](http://bl.ocks.org/Fil/d9752d8c41cc2cc176096ce475233966)

In the example above, we assign _n_ points to a grid of _n_ positions. `costs[i][j]` is the square distance between point _i_'s original coordinates and position _j_'s coordinates. The algorithm minimizes the total cost, i.e. the sum of square displacements.


## 

Comments and patches at [Fil/lap-jv](https://github.com/Fil/lap-jv).
