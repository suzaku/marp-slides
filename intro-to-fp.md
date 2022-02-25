---
marp: true
theme: gaia
paginate: true
backgroundImage: url('https://marp.app/assets/hero-background.svg')
backgroundColor: #fff
---

![bg left:40% 80%](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8f/Orange_lambda.svg/354px-Orange_lambda.svg.png?20080430163557)

# Introduction to Functional Programming ~~with Elixir~~

Xuecong Liao

---

## What is Functional Programming?

FP is about writing programs with ~~ONLY~~ pure functions.

---

## What are pure functions?

Functions that have no side-effects, they just take inputs and return outputs.

```ruby
irb(main):017:0> arr = [1, 2, 3]
=> [1, 2, 3]
irb(main):018:0> arr.push(2) # Not pure, ❌
=> [1, 2, 3, 2]
irb(main):019:0> arr
=> [1, 2, 3, 2]
irb(main):020:0> arr.uniq # Pure, ✅
=> [1, 2, 3]
irb(main):021:0> arr
=> [1, 2, 3, 2]
```

---

## How to make a function pure?

```python
import datetime

events = []

# Is this function pure?
def track_event(event_type):
    event = {
        "type": event_type,
        "time": datetime.datetime.now(),
    }
    global events
    events.append(event)
```

---

## How to make a function pure?

### Make all depedencies explicit.

```python
def track_event(events, event_type, time):
    event = {
        "type": event_type,
        "time": time,
    }
    return events + [event]
```

---

## Is Ruby a FP Language?

Obviously, we can program with pure functions like `Array#uniq` in Ruby, does this make it a FP language?

> A functional language actively helps you eliminate side-effects wherever possible, and tightly control them wherever it’s not.

---

## Immutable Variables

Every time a value is updated, a new value is returned.

```elixir
nums = [1, 3, 6, 7, 10]
List.delete(nums, 3) 
    |> List.insert_at(2, 33) 
    |> List.update_at(1, &(&1 + 10))
    |> Enum.map(fn x -> x * x end)
    |> Enum.dedup
    |> List.replace_at(3, 42)
    |> Enum.drop_every(2)
    |> List.foldl(0, &(&1 + &2))
# nums = ?
```


---

## But ... do we have to COPY a lot?

No, thanks to **Persistent Data Structures**.

> a persistent data structure is a data structure that always preserves the previous version of itself when it is modified.

---

## Persistent Data Structures Examples

```elixir
iex(12)> x = [3, 2, 1]
iex(13)> y = List.insert_at(x, 0, 4)
```

![linked lists concatenation](https://raw.githubusercontent.com/suzaku/marp-slides/main/concat-linked-list.svg?token=GHSAT0AAAAAABRNZVT5JO3Y2NVGXMCPI7U6YQVU26A)

---

## Benefits of Pure Functions

1. Memoization
1. Precomputation at build time
1. Threadsafe by definition
1. No more flaky tests

---

## Resources

- https://elixir-lang.org/
- https://exercism.org/tracks/elixir
- https://elm-lang.org/
- [What is Functional Programming?](http://blog.jenkster.com/2015/12/what-is-functional-programming.html)
- [Functional Programming in 40 Minutes](https://www.youtube.com/watch?v=0if71HOyVjY)

---

## Thank You