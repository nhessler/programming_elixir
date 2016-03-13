Exercise StringsAndBinaries-4
=============================

```elixir

# (Hard) Write a function that takes a single-quoted string of the
# form number [+-*/] number and returns the result of the calculation.
# The individual numbers do not have leading plus or minus signs.
#
#   calculate(’123 + 27’) # => 150


defmodule StringMath do

  def calculate(lst) do
    [num1, ' ', action, ' ', num2] = Enum.chunk_by(lst, &(&1 == ?\s))
    _calculate(_get_integer(num1), action, _get_integer(num2))
  end

  defp _calculate(num1, '+', num2), do: num1 + num2
  defp _calculate(num1, '-', num2), do: num1 - num2
  defp _calculate(num1, '*', num2), do: num1 * num2
  defp _calculate(num1, '/', num2), do: div(num1, num2)

  defp _get_integer(number) do
    {int, []} = :string.to_integer(number)

    int
  end
end

```
