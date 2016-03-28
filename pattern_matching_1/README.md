Exercise PatternMatching-1
==========================

### Question

Which of the following will match?

* `a = [1, 2, 3]`
* `a = 4`
* `4 = a`
* `[a, b] = [ 1, 2, 3 ]`
* `a = [ [ 1, 2, 3 ] ]`
* `[a] = [ [ 1, 2, 3 ] ]`
* `[[a]] = [ [ 1, 2, 3 ] ]`


### Answer

```elixir

a = [1, 2, 3]       # Matches, a set to [1, 2, 3]
a = 4               # Matches, a set to 4
4 = a               # Matches
[a, b] = [1, 2, 3]  # Doesn't Match, Match Error
a = [[1, 2, 3]]     # Matches, a set to [[1, 2, 3]]
[a] = [[1, 2, 3]]   # Matches, a set to [1, 2, 3]
[[a]] = [[1, 2, 3]] # Doesn't Match, Match Error

```
