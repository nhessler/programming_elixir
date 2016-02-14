Exercise ListsAndRecursion-2
============================

```elixir

# Write a max(list) that returns the element with the maximum value in
# the list. (This is slightly trickier than it sounds.)

defmodule MyList do
  def max_el([head | tail]), do: _max_el(tail, head)
  def _max_el([], val), do: val
  def _max_el([ head | tail ], val) when head > val, do: _max_el(tail, head)
  def _max_el([ _head | tail ], val), do: _max_el(tail, val)
end

```
