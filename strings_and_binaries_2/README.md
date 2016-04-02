Exercise StringsAndBinaries-2
=============================

### Question

Write an **anagram?(word1, word2)** that returns true if its parameters are anagrams.


### Answer

```elixir

# Write an anagram?(word1, word2) that returns true if its parameters
# are anagrams.

defmodule MyString do

  def anagram?(word1, word2) do
    _arrange(word1) == _arrange(word2)
  end

  defp _arrange(word) do
    word |> String.downcase |> to_char_list |> Enum.sort()
  end
end


```
