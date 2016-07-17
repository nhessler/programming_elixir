Exercise OTP-Servers-2
======================

### Question

Extend your stack server with a **push** interface that adds a single value to the top of the stack. This will be implemented as a cast.

Experiment in iex with pushing and popping values.


### Answer

``` elixir

defmodule MyStack do
  use GenServer

  def handle_call(:pop, _from, [h | t]) do
    {:reply, h, t}
  end

  def handle_cast({:push, item}, stack) do
    {:noreply, [item | stack]}
  end
end

```
