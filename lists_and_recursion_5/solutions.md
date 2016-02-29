Exercise ListsAndRecursion-5
============================

```elixir

# Implement the following Enum functions using no library functions or
# list comprehensions: all?, each, filter, split, and take. You may
# need to use an if statement to implement filter. The syntax for this
# is
#
#	​if​ condition ​do​
​#	  expression(s)
​#	​else​
​#	  expression(s)
​#	​end​

defmodule MyEnum do
  def all?(list, func \\ &(!!&1))
  def all?(list, func), do: _all?(list, func, true)

  defp _all?(_, _, false),           do: false
  defp _all?([], _, _),              do: true
  defp _all?([head | tail], func, _) do
    _all?(tail, func, !!func.(head))
  end

  def each([], _),              do: :ok
  def each([head | tail], func) do
    func.(head)
    each(tail, func)
  end

  def filter(list, func), do: _filter(MyEnum.reverse(list), func, [], false, nil)

  defp _filter([], _, selected, false, _),               do: selected
  defp _filter([], _, selected, true, val),              do: [val | selected]
  defp _filter([head | tail], func, selected, false, _)  do
    _filter(tail, func, selected, func.(head), head)
  end
  defp _filter([head | tail], func, selected, true, val) do
    _filter(tail, func, [val | selected], func.(head), head)
    end

  def split(list, count) when count >= 0,                do: _split(list, [], count)
  def split(list, count) when length(list) > abs(count), do: _split(list, [], length(list) + count)
  def split(list, _),                                    do: _split(list, [], 0)

  defp _split([], front, _),               do: [MyEnum.reverse(front), []]
  defp _split(list, front, 0),             do: [MyEnum.reverse(front), list]
  defp _split([head | tail], front, count) do
    _split(tail, [head | front], count - 1)
  end

  def take(list, count) when count >= 0, do: split(list, count) |> hd
  def take(list, count),                 do: split(list, count) |> tl |> hd

  def reverse(list), do: _reverse(list, [])

  defp _reverse([], reversed),            do: reversed
  defp _reverse([head | tail], reversed), do: _reverse(tail, [head | reversed])
end


```
