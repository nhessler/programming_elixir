Exercise ListsAndRecursion-4
============================

```elixir

# Write a function MyList.span(from, to) that returns a list of the
# numbers from 'from' up to 'to'.

defmodule MyList do

  def span(from, to, lst \\ [])
  def span(from, to, lst) when from < to do
    span(from, to - 1, [to | lst] )
  end
  def span(to, to, lst) do
    [ to | lst ]
  end

end

```
