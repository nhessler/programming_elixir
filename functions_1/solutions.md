Exercise Functions-1
====================

```elixir

# list_concat.([:a, :b], [:c, :d]) #=> [:a, :b, :c, :d]
list_concat = fn l1, l2 -> l1 ++ l2 end

# sum.(1, 2, 3) #=> 6
sum = fn a, b, c -> a + b + c end

# pair_tuple_to_list.({1234, 5678}) #=>[1234, 5678]
pair_tuple_to_list = fn {1234, 5678} -> [1234, 5678] end

```
