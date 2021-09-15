# Pizza Branches Finder
As a Pizza restaurant we need to optimize delivery cost and ensure that customers will get their order delivered as fast as possible. When a customer places an order we would like to find the closest branch which can serve the customer's order.

Our city is a 2D-Grid system and divided into 10 x 10 blocks. A driver can only drive in vertical and horizontal direction. When they drive across a block the cost of delivery is plus by 1, but when they need to turn the across the block delivery cost will be plus by 2.

For example a branch is located at **[ 1, 3 ]** (X) and needs to deliver pizza to a customer located at **[ 7, 5 ]** (Y) the delivery cost will be **9**, the calculation is look like this

```
     1    2    3    4    5    6    7    8    9    10
   ┏━━━━┳━━━━┳━━━━┳━━━━┳━━━━┳━━━━┳━━━━┳━━━━┳━━━━┳━━━━┓
1  ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
2  ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
3  ┃ (X)╋━+1━╋━+1━╋━+1━╋━+1━╋━+1━╋━+2 ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━╋━╋━━━━╋━━━━╋━━━━┫
4  ┃    ┃    ┃    ┃    ┃    ┃    ┃ +1 ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━╋━╋━━━━╋━━━━╋━━━━┫
5  ┃    ┃    ┃    ┃    ┃    ┃    ┃ (Y)┃ +1 ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
6  ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
7  ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
8  ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
9  ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┣━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━╋━━━━┫
10 ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃    ┃
   ┗━━━━┻━━━━┻━━━━┻━━━━┻━━━━┻━━━━┻━━━━┻━━━━┻━━━━┻━━━━┛
```

In addition each restaurant also has a limited amount of pizza in their stock, only a restaurant which has enough pizza can deliver the customer’s order.

## Requirements
- Please create a function named branchesFinder .
- This function requires 2 arguments:
- First argument is an array of a restaurant branch's objects containing name, location and currentStock, example:
  ```js
  [
    { name: “Ladprao”, location: [3, 4], currentStock: 5 },
    ...
  ]
  ```
- Second argument is the customer's order object containing customer’s location and amount of ordered pizza, example:
  ```js
  { location: [5, 7], amount: 1 }
  ```
- This function will calculate and return the branch(s) which has the cheapest delivery cost and has enough pizza to deliver
  - When multiple branches have the same delivery cost, pick the branch which has the most currentStock
  - When multiple branches have the same delivery cost and currentStock, pick the branch whose name comes first in alphanumeric order.
  - When there are no branches that have enough stock to deliver a customer order, return multiple branches from the cheapest one until it fulfill customer’s order
  - When there are no branches that have enough stock to deliver even combined all branches stock, return an empty array.
- This function must return the arrays branches to delivering the customer order with object containing the restaurant branch name, location, delivery cost, and amount of pizza to deliver in this format
  ```js
  { name: “Ladprao”, location: [5, 7], deliveryCost: 6, amount: 2 }
  ```

## Test Cases
```js
branchesFinder()

// ----------------------------------------------------------------
// Test case #1
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [2, 4], currentStock: 5 },
    { name: "Ekkamai", location: [7, 8], currentStock: 5 },
  ],
  { location: [6, 7], amount: 2 }
)
// Return
[{ name: "Ekkamai", location: [7, 8], deliveryCost: 3, amount: 2 }]

// ----------------------------------------------------------------
// Test case #2 : No turn less cost
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [2, 3], currentStock: 4 },
    { name: "Ekkamai", location: [6, 7], currentStock: 4 },
  ],
  { location: [7, 3], amount: 2 }
)
// Return
[{ name: "Ladprao", location: [2, 3], deliveryCost: 5, amount: 2 }]


// ----------------------------------------------------------------
// Test case #3 : Cheapest has not enough pizza
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [2, 4], currentStock: 3 },
    { name: "Ekkamai", location: [7, 8], currentStock: 5 },
    { name: "Bangmod", location: [6, 4], currentStock: 5 },
  ],
  { location: [3, 4], amount: 4 }
)
// Return
[{ name: "Bangmod", location: [6, 4], deliveryCost: 3, amount: 4 }]

// ----------------------------------------------------------------
// Test case #4 : Same delivery cost
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [3, 4], currentStock: 5 },
    { name: "Ekkamai", location: [2, 3], currentStock: 4 },
    { name: "Bangmod", location: [6, 4], currentStock: 5 },
  ],
  { location: [1, 7], amount: 3 }
)
// Return
[{ name: "Ladprao", location: [3, 4], deliveryCost: 6, amount: 3 }]

// ----------------------------------------------------------------
// Test case #5 : Same delivery cost, same stock
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [3, 4], currentStock: 5 },
    { name: "Ekkamai", location: [2, 3], currentStock: 5 },
    { name: "Bangmod", location: [6, 4], currentStock: 5 },
  ],
  { location: [1, 7], amount: 3 }
)
// Return
[{ name: "Ekkamai", location: [2, 3], deliveryCost: 6, amount: 3 }]

// ----------------------------------------------------------------
// Test case #6 : Need to deliver from multiple branches
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [8, 9], currentStock: 5 },
    { name: "Ekkamai", location: [3, 3], currentStock: 4 },
    { name: "Bangmod", location: [5, 8], currentStock: 5 },
  ],
  { location: [1, 7], amount: 7 }
)

// Return
[
  { name: "Bangmod", location: [3, 3], deliveryCost: 6, amount: 5 },
  { name: "Ekkamai", location: [3, 3], deliveryCost: 7, amount: 2 },
]

// ----------------------------------------------------------------
// Test case #7 : Cannot deliver
// ----------------------------------------------------------------
branchesFinder(
  [
    { name: "Ladprao", location: [2, 3], currentStock: 7 },
    { name: "Ekkamai", location: [7, 6], currentStock: 3 },
    { name: "Bangmod", location: [6, 4], currentStock: 2 },
  ],
  { location: [8, 9], amount: 20 }
)

// Return
[]


```
