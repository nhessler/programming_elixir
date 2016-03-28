Exercise ListsAndRecursion-3
============================

### Question

An Elixir single-quoted string is actually a list of individual character codes. Write a `caesar(list, n)` function that adds n to each list element, wrapping if the addition results in a character greater than *z*.

```shell

​iex>​ MyList.caesar(​'ryvkve'​, 13)
?????? :)

```


### Answer

```elixir

defmodule MyList do

  def caesar([], _), do: ''
  def caesar([ head | tail ], n) when head + n > ?z do
    [head - (26 - n) | caesar(tail, n)]
  end
  def caesar([ head | tail ], n), do: [(head + n) | caesar(tail, n)]

end

MyList.caesar('ryvkve', 13) #=> 'elixir'

```
