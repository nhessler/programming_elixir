Exercise ControlFlow-2
======================

### Question

We now have three different implementations of FizzBuzz. One uses **cond**, one uses **case**, and one uses separate functions with guard clauses.

Take a minute to look at all three. Which do you feel best expresses the problem. Which will be easiest to maintain?

The **case** style and the implementation using guard clauses are different from control structures in most other languages. If you feel that one of these was the best implementation, can you think of ways to remind yourself to investigate these options as you write Elixir code in the future?


### Answer

They all seem to be similar, but for this situation I like the **case** statement. each **case** is on one line thus making it easier to see the conditions and clauses. That said, if this were not on one line I think the functions with guard clauses would be better. so maybe **case** statements when you have conditions that just return values and functions with guard clauses if those conditions require logic be executed.
