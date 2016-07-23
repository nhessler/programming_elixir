Exercise OTP-Supervisors-1
==========================

### Question

Add a supervisor to your stack application. Use iex to make sure it starts the server correctly. Use the server normally, and then crash it (try popping from an empty stack). Did it restart? What were the stack contents after the restart?


### Answer

``` elixir

defmodule MyStack do
  use Application

  def start(_type, _args) do
    import Supervisor.Spec, warn: false

    children = [
      worker(MyStack.Server, [5, "cat", 9])
    ]

    opts = [strategy: :one_for_one, name: MyStack.Supervisor]

    Supervisor.start_link(children, opts)
  end
end

defmodule MyStack.Server do
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
