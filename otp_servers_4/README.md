Exercise OTP-Servers-4
======================

### Question

Add the API to your stack module (the functions that wrap the **GenServer** calls).


### Answer

``` elixir

defmodule MyStack do
  use GenServer

  # External API

  def start_link(stack), do:
    GenServer.start_link(__MODULE__, stack, name: __MODULE__)

  def pop, do: GenServer.call(__MODULE__, :pop)

  def push(item), do: GenServer.cast(__MODULE__, {:push, item})

  # GenServer API

  def handle_call(:pop, _from, [h | t]) do
    {:reply, h, t}
  end

  def handle_cast({:push, item}, stack) do
    {:noreply, [item | stack]}
  end
end

```
