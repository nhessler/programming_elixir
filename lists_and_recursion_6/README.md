Exercise ListsAndRecursion-6
============================

### Question

(Hard) Write a `flatten(list)` function that takes a list that may contain any number of sublists, which themselves may contain sublists, to any depth. It returns the elements of these lists as a flat list.

```shell

​iex>​ MyList.flatten([ 1, [ 2, 3, [4] ], 5, [[[6]]]])
[1,2,3,4,5,6]

```

*Hint: You may have to use `Enum.reverse` to get your result in the correct order.*


### Answer

```elixir

defmodule MyEnum do

  def flatten(list), do: _flatten(list, [])

  defp _flatten([], flattened),           do: MyEnum.reverse(flattened)
  defp _flatten([[] | tail], flattened),  do: _flatten(tail, flattened)
  defp _flatten([head | tail], flattened) when is_list(head) do
    _flatten([hd(head), tl(head) | tail], flattened)
  end
  defp _flatten([head | tail], flattened), do: _flatten(tail, [head | flattened])


  def reverse(list), do: _reverse(list, [])

  defp _reverse([], reversed),            do: reversed
  defp _reverse([head | tail], reversed), do: _reverse(tail, [head | reversed])

end

```
