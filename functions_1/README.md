Exercise Functions-1
====================

### Question

Go into iex. Create and run the functions that do the following:

* `list_concat.([:a, :b], [:c, :d]) #=> [:a, :b, :c, :d]`
* `sum.(1, 2, 3) #=> 6`
* `pair_tuple_to_list.( { 1234, 5678 } ) #=> [ 1234, 5678 ]`


### Answer

```elixir

list_concat = fn l1, l2 -> l1 ++ l2 end

sum = fn a, b, c -> a + b + c end

pair_tuple_to_list = fn {1234, 5678} -> [1234, 5678] end

```
