Exercise ListsAndRecursion-1
============================

### Question

Write a `mapsum` function that takes a list and a function. It applies the function to each element of the list and then sums the result, so

```shell

​iex>​ MyList.mapsum [1, 2, 3], &(&1 * &1)
14

```


### Answer

```elixir

defmodule MyList do
  def mapsum(list, func) do
    list
      |> Enum.map(func)
      |> Enum.reduce(0, &(&1 + &2))
  end
end

```
