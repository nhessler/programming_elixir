Exercise StringsAndBinaries-1
=============================

### Question

Write a function that returns **true** if a single-quoted string contains only printable ASCII characters (space through tilde).


### Answer

```elixir

defmodule Ascii do

  def all_printable?(list) do
    list |> Enum.all?(&(&1 in ?\s..?~))
  end

end


```
