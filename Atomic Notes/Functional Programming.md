---
id: Functional
created_date: 2024-09-29
updated_date: 2024-09-29
type: note
tags:
  - "#cpts355"
  - "#functionalprogramming"
  - "#haskell"
---

# Functional Programming

> A paradigm that treats computation as evaluating mathematical functions and avoids changing state and mutable data (as much as possible).

## Key Characteristics

- **Immutability**: Data is treated as constant and cannot be modified after creation.
- **Pure Functions**: Functions that consistently produce the same output for the same input and have no side effects.
- **Recursion**: A programming technique where a function calls itself to solve a problem
- **Higher-order Functions**: A function that either takes one or more functions as arguments or returns a function as its result.

## Important Higher Order Functions

The most important higher order functions in Haskell are `map`, `filter`, and the fold functions `foldl` and `foldr`.

### Map

The **map** function applies a function to every single element in a list.

```haskell
output = map (\x -> x + 1) input
```

![[Drawing 2024-09-29 12.01.52.excalidraw]]

### Filter

The **filter** function will remove every element of a list that returns false when given an input function.

```haskell
output = filter (\x -> isOdd x) input
```

![[Drawing 2024-09-29 12.10.42.excalidraw]]

### Fold

The two fold functions have a key difference. The side of the list they start folding from. The fold function takes three arguments: a function which takes an element of the list and the accumulator, the starting value of the accumulator, and the input list. Foldl starts folding from the left side and foldr starts folding from the right.

**Fold Illustrated**

![[Drawing 2024-09-29 12.18.08.excalidraw]]

## Fundamental Data Structures

## Monads

One important note about pure functions is that they always produce the same output regardless of input. As a consequence pure functions cannot have exception handling because exceptions are a side effect. To solve this we use **monads**.