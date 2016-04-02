Exercise StringsAndBinaries-6
=============================

### Question

Write a function to capitalize the sentences in a string. Each sentence is terminated by a period and a space. Right now, the case of the characters in the string is random.

```shell

​iex>​ capitalize_sentences(​"​​oh. a DOG. woof. "​)
"Oh. A dog. Woof."

```


### Answer

```elixir

defmodule MyString do

  def capitalize_sentences(string), do: _capitalize_sentences(string, "", true)

  defp _capitalize_sentences(<<>>, result, _capitalize), do: result
  defp _capitalize_sentences(<< ". ",  tail :: binary >> , result, _capitalize) do
    _capitalize_sentences(tail, "#{result}. ", true)
  end
  defp _capitalize_sentences(<< " ", tail :: binary >>, result, capitalize) do
    _capitalize_sentences(tail, "#{result} ", capitalize)
  end
  defp _capitalize_sentences(<< head :: utf8, tail :: binary >>, result, false) do
    _capitalize_sentences(tail, "#{result}#{String.downcase(List.to_string([head]))}", false)
  end
  defp _capitalize_sentences(<< head :: utf8, tail :: binary >>, result, true) do
    _capitalize_sentences(tail, "#{result}#{String.capitalize(List.to_string([head]))}", false)
  end

end

```
