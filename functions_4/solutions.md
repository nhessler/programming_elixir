Exercise Functions-4
====================

```elixir

# Write a function prefix that takes a string. It should return a new
# function that takes a second string. When that second function is
# called, it will return a string containing the first string, a
# space, and the second string.

# Example:
#   mrs = prefix.("Mrs")
#   mrs.("Smith")
#   #=> "Mrs Smith"
#   prefix.("Elixir").("Rocks")
#   #=> "Elixir Rocks"

prefix = fn head ->
           fn tail ->
             "#{head} #{tail}"
           end
         end

```
