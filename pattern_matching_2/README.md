Exercise PatternMatching-2
==========================

### Question

Which of the following will match?

* `[ a, b, a ] = [ 1, 2, 3 ]`
* `[ a, b, a ] = [ 1, 1, 2 ]`
* `[ a, b, a ] = [ 1, 2, 1 ]`


### Answer

```elixir

[a, b, a] = [1, 2, 3] # Doesn't Match, Match Error
[a, b, a] = [1, 1, 2] # Doesn't Match, Match Error
[a, b, a] = [1, 2, 1] # Matches, a set to 1 and b set to 2

```
