Exercise PatternMatching-3
==========================

```elixir

a = 2 # setup

[a, b, a] = [1, 2, 3] # Doesn't Match, Match Error
[a, b, a] = [1, 1, 2] # Doesn't Match, Match Error
a = 1                 # Matches, a set to 1
^a = 2                # Doesn't Match, Match Error
^a = 1                # Matches
^a = 2 - a            # Matches

```
