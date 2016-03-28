Exercise ListsAndRecursion-0
============================

### Question

I defined our `sum` function to carry a partial total as a second parameter so I could illustrate how to use accumulators to build values. The `sum` function can also be written without an accumulator. Can you do it?


### Answer

```elixir

defmodule MyList do
  def sum([]), do: 0
  def sum([ total | [] ]), do: total
  def sum([ total | [ adder | tail ]]) do
    sum([ total + adder | tail])
  end
end

```
