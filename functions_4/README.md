Exercise Functions-4
====================

### Question

Write a function prefix that takes a string. It should return a new function that takes a second string. When that second function is called, it will return a string containing the first string, a space, and the second string.

```shell

​iex> mrs = prefix.(​"​​Mrs"​)
​#Function<erl_eval.6.82930912>​
iex> mrs.(​"​​Smith"​)
​"​​Mrs Smith"​
iex> prefix.(​"​​Elixir"​).(​"​​Rocks"​)
​"​​Elixir Rocks"​

```


### Answer

```elixir

prefix = fn head ->
           fn tail ->
             "#{head} #{tail}"
           end
         end

```
