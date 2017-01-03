## LAP-JV
### Linear Assignment Problem — algorithm by R. Jonker and A. Volgenant

Ported to javascript by Philippe Rivière, from the C++ implementation found at https://github.com/yongyanghz/LAPJV-algorithm-c

Added an epsilon to avoid infinite loops caused by rounding errors.

The algorithm runs in `O(n^2)`. It is better run in a javascript worker, as in the following example:

[![](https://gist.githubusercontent.com/Fil/d9752d8c41cc2cc176096ce475233966/raw/88c1e7e4d62df8145a68808b7252cd5013e0394f/thumbnail.png)](http://bl.ocks.org/Fil/d9752d8c41cc2cc176096ce475233966)

## Usage

```javascript
  const n = 3, costs = [[3,2,1], [1,2,3], [2,2,2]];
  const solution = lap(n, costs);

  console.log(solution.col);
  // [1, 2, 0]

```

Comments and patches at [Fil/lap-jv](https://github.com/Fil/lap-jv).