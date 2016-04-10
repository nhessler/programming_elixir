Exercise WorkingWithMultipleProcesses-1
=======================================

### Question

Run this code on your machine. See if you get comparable results.


### Answer

yes I got similar linear results as well.

``` shell

$ elixir -r chain.ex -e "Chain.run(10)"
{3723, "Result is 10"}

$ elixir -r chain.ex -e "Chain.run(100)"
{2526, "Result is 100"}

$ elixir -r chain.ex -e "Chain.run(1_000)"
{12240, "Result is 1000"}

$ elixir -r chain.ex -e "Chain.run(10_000)"
{124650, "Result is 10000"}

$ elixir -r chain.ex -e "Chain.run(100_000)"
{1061573, "Result is 100000"}

$ elixir --erl "+P 1000000" -r chain.ex -e "Chain.run(400_000)"
{3460427, "Result is 400000"}

$ elixir --erl "+P 1000000" -r chain.ex -e "Chain.run(1_000_000)"
{9384272, "Result is 1000000"}

```
