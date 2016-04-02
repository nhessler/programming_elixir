Exercise ControlFlow-1
======================

### Question

Rewrite the FizzBuzz example using case.


### Answer

```elixir

defmodule Fizzbuzz do

  def upto(n) when n > 0, do: 1..n |> Enum.map(&(fizzbuzz(&1)))

  defp fizzbuzz(n) when n > 0 do
    case n do
      n when rem(n, 3) == 0 and rem(n, 5) == 0 -> "FizzBuzz"
      n when rem(n, 3) == 0                    -> "Fizz"
      n when rem(n, 5) == 0                    -> "Buzz"
      n                                        -> n
    end
  end

end

```
