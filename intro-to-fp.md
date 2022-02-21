---
marp: true
theme: uncover
_class: invert
---

# Introduction to Functional Programming

Xuecong Liao

---

## What is Functional Programming?

> functional programming is all about building functions for immutable variables.
from [Ari Joury](https://towardsdatascience.com/why-developers-are-falling-in-love-with-functional-programming-13514df4048e)

---

## Pure Functions

Functions that have no side-effects, they just take inputs and return outputs.

```ruby
irb(main):017:0> arr = [1, 2, 3]
=> [1, 2, 3]
irb(main):018:0> arr.push(2)
=> [1, 2, 3, 2]
irb(main):019:0> arr
=> [1, 2, 3, 2]
irb(main):020:0> arr.uniq
=> [1, 2, 3]
irb(main):021:0> arr
=> [1, 2, 3, 2]
```

---

## Immutable Variables

```elixir
nums = [3, 40, 22]
List.delete(nums, 3) 
    |> List.insert_at(2, 33) 
    |> List.update_at(1, &(&1 + 10))
    |> List.replace_at(3, 42)
    |> List.foldl(0, &(&1 + &2))
# nums = ?
```

---

## Persistent Data Structures

---

## Why Pure Functions?


---

## Resources

- https://elixir-lang.org/
- [Functional Programming in 40 Minutes](https://www.youtube.com/watch?v=0if71HOyVjY)

---

## Thank You