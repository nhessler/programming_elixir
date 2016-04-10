Exercise WorkingWithMultipleProcesses-7
=======================================

### Question

Change the **^pid** in **pmap** to **_pid**. This means the receive block will take responses in the order the processes send them. Now run the code again. Do you see any difference in the output? If you’re like me, you don’t, but the program clearly contains a bug. Are you scared by this? Can you find a way to reveal the problem (perhaps by passing in a different function, by sleeping, or by increasing the number of processes)? Change it back to **^pid** and make sure the order is now correct.”


### Answer

for **1..10** I got the correct answer. I was able to get the wrong answer by doing **1..1000** but not consistently. I added a 1 second **sleep** to the spawned processes to get the wrong answer consistently. It was fixed by going back to **^pid**

``` elixir

defmodule Parallel do
  def pmap(collection, fun) do
    me = self
    collection
    |> Enum.map(fn (elem) ->
        spawn_link fn -> (:timer.sleep(1000); send me, {self, fun.(elem) }) end
      end)
    |> Enum.map(fn (pid) ->
        receive do { ^pid, result } -> result end
      end)
  end
end

```
