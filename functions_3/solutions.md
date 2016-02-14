Exercise Functions-3
====================

```elixir

# The operator rem(a, b) returns the remainder after dividing a by b.
# Write a function that takes a single integer (n) and calls the
# function in the previous exercise, passing it rem(n,3), rem(n,5),
# and n. Call it seven times with the arguments 10, 11, 12, and so on.
# You should get “Buzz, 11, Fizz, 13, 14, FizzBuzz, 16."
#
# (Yes, it’s a FizzBuzz solution with no conditional logic.)

fizzbuzz_matcher = fn
  0, 0, _ -> "FizzBuzz."
  0, _, _ -> "Fizz."
  _, 0, _ -> "Buzz."
  _, _, n -> n
end

fizzbuzz = fn
  n -> fizzbuzz_matcher.(rem(n, 3), rem(n, 5), n)
end

fizzbuzz.(10) #=> "Buzz."
fizzbuzz.(11) #=> 11
fizzbuzz.(12) #=> "Fizz."
fizzbuzz.(13) #=> 13
fizzbuzz.(14) #=> 14
fizzbuzz.(15) #=> "FizzBuzz."
fizzbuzz.(16) #=> 16

```
