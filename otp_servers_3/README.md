Exercise OTP-Servers-3
======================

### Question

Give your stack server process a name, and make sure it is accessible by that name in iex


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

GenServer.start_link(MyStack, [5, "cat", 9], name: MyStack)
:sys.get_status MyStack

```
