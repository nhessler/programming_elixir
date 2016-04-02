Exercise StringsAndBinaries-5
=============================

### Question

Write a function that takes a list of dqs and prints each on a separate line, centered in a column that has the width of the longest string. Make sure it works with UTF characters.

```shell

​iex>​ center([​"​​cat"​, ​"​​zebra"​, ​"​​elephant"​])
  cat
 zebra
elephant

```


### Answer

```elixir

# Write a function that takes a list of dqs and prints each on a
# separate line, centered in a column that has the width of the longest
# string. Make sure it works with UTF characters.
#
​#	​iex>​ center([​"​​cat"​, ​"​​zebra"​, ​"​​elephant"​])
#​	  cat
#	 zebra
#	elephant


defmodule MyString do

  def center(dqs_lst) do
    max_length = Enum.max_by(dqs_lst, &String.length(&1)) |> String.length
    Enum.each(dqs_lst, &(centered_print(&1, max_length)))
  end

  def centered_print(dqs, line_length) do
    str_length = div(line_length + String.length(dqs), 2)

    dqs |> String.rjust(str_length) |> IO.puts
  end
end


```
