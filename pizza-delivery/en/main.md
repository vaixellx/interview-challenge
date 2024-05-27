<p style="text-align: right">
  <a href="https://vaixellx.github.io/interview-challenge/pizza-delivery/th/main">ไทย</a>
  |
  <a href="https://vaixellx.github.io/interview-challenge/pizza-delivery/en/main">English</a>
</p>

---

# Pizza Hat

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
- Please create a function named `branches_finder` to calculate the best branch to deliver pizza to customer.
- This function will requires 2 arguments.
- First argument is an array of a restaurant branch's objects containing name, location and `current_stock`, example:
  ```ruby
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 }
  ]
  ```
- Second argument is the customer's order object containing customer’s location and amount of ordered pizza, example:
  ```ruby
  { location: [4, 7], amount: 2 }
  ```
- This function will calculate and return the branch which has the cheapest delivery cost and has enough pizza to deliver
  - When multiple branches have the same delivery cost, pick the branch which has the lowest `current_stock`
  - When multiple branches have the same delivery cost and `current_stock`, pick the branch which name comes first in alphanumeric order.
  - When there are no branches that have enough stock to deliver a customer order, raise an error.
- This function must return the branch to delivering the customer order as object containing the restaurant branch name, location, delivery cost, and stock left after processing customer's order in this format
  ```ruby
  { name: "Ekkamai", location: [4, 7], delivery_cost: 3, current_stock: 1 }
  ```

## Test Cases

```ruby
# ----------------------------------------------------------------
#  Test case #1
# ----------------------------------------------------------------
branches_finder(
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 }
  ],
  { location: [4, 7], amount: 2 }
)

# return
{ name: "Ekkamai", location: [7, 7], delivery_cost: 3, current_stock: 1 }

# ----------------------------------------------------------------
#  Test case #2 : With turn
# ----------------------------------------------------------------
branches_finder(
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 }
  ],
  { location: [3, 7], amount: 2 }
)

# return
{ name: "Ekkamai", location: [7, 7], delivery_cost: 4, current_stock: 1 }

# ----------------------------------------------------------------
#  Test case #3 : Cheapest has not enough pizza
# ----------------------------------------------------------------
branches_finder(
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 }
  ],
  { location: [3, 7], amount: 4 }
)

# return
{ name: "Ladprao", location: [2, 4], delivery_cost: 5, current_stock: 1 }

# ----------------------------------------------------------------
#  Test case #4 : Same delivery cost
# ----------------------------------------------------------------
branches_finder(
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 },
    { name: "Bangmod", location: [3, 8], current_stock: 4 }
  ],
  { location: [6, 8], amount: 2 }
)

# return
{ name: "Ekkamai", location: [7, 7], delivery_cost: 3, current_stock: 1 }

# ----------------------------------------------------------------
#  Test case #5 : Same delivery cost, same stock
# ----------------------------------------------------------------
branches_finder(
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 },
    { name: "Bangmod", location: [3, 8], current_stock: 3 }
  ],
  { location: [6, 8], amount: 2 }
)

# return
{ name: "Bangmod", location: [3, 8], delivery_cost: 3, current_stock: 1 }

# ----------------------------------------------------------------
#  Test case #6 : Cannot deliver
# ----------------------------------------------------------------
branches_finder(
  [
    { name: "Ladprao", location: [2, 4], current_stock: 5 },
    { name: "Ekkamai", location: [7, 7], current_stock: 3 },
    { name: "Bangmod", location: [3, 8], current_stock: 4 }
  ],
  { location: [6, 8], amount: 7 }
)

# raise error
RuntimeError: Cannot deliver
```
