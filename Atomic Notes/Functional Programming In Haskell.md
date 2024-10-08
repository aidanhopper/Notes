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

# Functional Programming In Haskell

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

*Note: in javascript the `fold` functions are combined into the `reduce` function.*

**Fold Illustrated**

![[Drawing 2024-09-29 12.18.08.excalidraw]]

## Fundamental Data Structures

The two fundamental data structures in haskell are the list and the tuple. Lists are **homogeneous** meaning they are a collection of elements of the *same* type. They can also grow dynamically using the `++` and `:` functions because the underlying structure is a persitent data structure (only works because of immutability). Tuples are a fixed-size collection of elements which *can* be different types.

A **persistent data structure** is a linked list that is assigned labels. When prepending to a list and assigning it a new label such as

```haskell
a = [1, 2, 3, 4]
b = 0:a
```

where only one new node in the linked list has to be allocated because the presistent data structure now looks like this.

![[Drawing 2024-09-29 12.36.20.excalidraw]]

When appending the list with another list

```haskell
a = [1, 2, 3, 4]
b = a ++ [5, 6]
```

the persisent data structure has to create a copy of the previous list in memory like this.

![[Drawing 2024-09-29 12.44.14.excalidraw]]

## List Comprehension

List comprehension is a concise way to construct lists.

```haskell
[expression | element <- list, condition]
```

You can even have multiple generators to iterate over multiple lists.

```ghci
[(x, y) | x <- [1..3], y <- [4..6]]
[(1,4),(1,5),(1,6),(2,4),(2,5),(2,6),(3,4),(3,5),(3,6)]
```

## Lazy Evaluation

Haskell uses lazy evaluation, meaning expressions are *only* evaluated when needed. This enables Haskell to generate infinite lists without running out of memory. To implement this Haskell uses a **thunk**, a deferred computation. This means a expression is ready to be evaluated when needed but only evaluated when something else requires it. 

This has two big benefits: increased performance and efficient processing of large structures. The drawbacks are that there is some performance overhead and it is harder to debug.

## Types

Types categorize values based on the  data they hold. There are three different ways to define types in haskell. One is using the `type` keyword which creates an alias for other types.

```haskell
type Name = String
type Age = Int

greet :: Name -> Age -> String
greet name age = "Hello, " ++ name ++ ", You are " ++ show age ++ " years old."
```

Another way to create types is using the `newtype` keyword which defines a distinct type from an existing type.

```haskell
newtype Age = Age Int
newtype Name = Name String

showAge :: Age -> String
showAge (Age a) = "Age is: " ++ show a
```

`newtype` allows you to differenciate between types with the same underlying structure for added type safety.

The last way to create types is using the `data` keyword which defines *algebraic data types*.

```haskell
data Shape = Rectangle Float Float | Square Float

area :: Shape -> Float
area (Rectangle width height) = width * height
area (Squarea side) = side * side
```

This can be used to create recursive data types for a tree or other structures.

## Functors, Applicatives, and Monads

One important note about pure functions is that they always produce the same output regardless of input. As a consequence pure functions cannot have exception handling because exceptions are a side effect. To solve this we use **monads** (& applicatives & functors).

Think of a monad as another universe, where every type in the normal universe has a alternative in the monad universe. We will use the Maybe monad as an example.

![[Drawing 2024-09-29 13.30.05.excalidraw]]

To alternate types between these two universes we can use maybe specific functions. One such function is `fmap` which takes a function in the normal universe and **lifts** it to the maybe universe `fmap (int -> int) = M int -> M int`. 

A **functor** is a type class that allows you to map a function over a wrapped value which is part of what a monad implements. 

The **applicative** function `<*>` unwraps a `M (int -> int)` function into `M int -> M int`. This can then take a `M int` as input and produce a `M b` as output. The function `pure` takes any argument and lifts it `pure (int -> int) = M (int -> int)`. 

A monad implements the **bind**  `>>=` operation which takes a function `a -> M b` which crosses the universe boundaries and rotates it to be `M a -> M b`

For example

```haskell
recip :: (Eq a, Fractional a) => a -> Maybe a
recip x
	| x == 0    = Nothing
	| otherwise = Just (1/x)

-- Just 10 >>= recip   returns 0.1
```
