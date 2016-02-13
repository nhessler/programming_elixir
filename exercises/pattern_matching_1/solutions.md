Exercise PatternMatching-1
==========================

```elixir

a = [1, 2, 3]       # Matches, a set to [1, 2, 3]
a = 4               # Matches, a set to 4
4 = a               # Matches
[a, b] = [1, 2, 3]  # Doesn't Match, Match Error
a = [[1, 2, 3]]     # Matches, a set to [[1, 2, 3]]
[a] = [[1, 2, 3]]   # Matches, a set to [1, 2, 3]
[[a]] = [[1, 2, 3]] # Doesn't Match, Match Error

```
