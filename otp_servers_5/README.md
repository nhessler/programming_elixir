Exercise OTP-Servers-5
======================

### Question

Implement the **terminate** callback in your stack handler. Use **IO.puts** to report the arguments it receives.

Try various ways of terminating your server. For example, popping an empty stack will raise an exception. You might add code that calls **System.halt(n)** if the **push** handler receives a number less than 10. (This will let you generate different return codes.) Use your imagination to try different scenarios.


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

  def handle_cast({:push, 69}, _stack), do: System.halt(69)
  def handle_cast({:push, item}, stack) do
    {:noreply, [item | stack]}
  end

  def terminate(reason, state) do
    IO.puts "CODE[#{inspect state}]: #{inspect reason}"
    :ok
  end
end

```
