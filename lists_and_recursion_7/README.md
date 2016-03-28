Exercise ListsAndRecursion-7
============================

### Question

In the last exercise of Chapter 7, ​*[Lists and Recursion](https://github.com/nhessler/programming_elixir/tree/master/lists_and_recursion_4)*​, you wrote a `span` function. Use it and list comprehensions to return a list of the prime numbers from 2 to *n*.


### Answer

```elixir

defmodule MyList do

  def span(from, to, lst \\ [])
  def span(from, to, lst) when from < to do
    span(from, to - 1, [to | lst] )
  end
  def span(to, to, lst) do
    [ to | lst ]
  end

  # not my solution. had to see it in forums
  # then was able to parse and understand algorithm
  def primes_up_to(n) do
    range = span(2, n)
    range -- (for a <- range, b <- range, a <= b, a*b <= n, do: a*b)
  end
end

```
