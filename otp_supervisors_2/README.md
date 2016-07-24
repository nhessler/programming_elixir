Exercise OTP-Supervisors-2
==========================

### Question

Rework your stack server to use a supervision tree with a separate stash process to hold the state. Verify that it works and that when you crash the server the state is retained across a restart.


### Answer

``` elixir

defmodule MyStack do
  use Application

  def start(_type, _args) do
    {:ok, _pid} = MyStack.Supervisor.start_link([5, "cat", 9])
  end
end

defmodule MyStack.Supervisor do
  use Supervisor

  def start_link(init_stack) do
    result = {:ok, sup} = Supervisor.start_link(__MODULE__, [init_stack])
    start_workers(sup, init_stack)

    result
  end

  def start_workers(sup, initial_stack) do
    {:ok, _stash} = Supervisor.start_child(sup, worker(MyStack.Stash, [initial_stack]))
    {:ok, _pid}   = Supervisor.start_child(sup, supervisor(MyStack.SubSupervisor, []))
  end

  def init(_) do
    supervise [], strategy: :one_for_one
  end
end

defmodule MyStack.SubSupervisor do
  use Supervisor

  def start_link() do
    {:ok, _pid} = Supervisor.start_link(__MODULE__, [])
  end

  def init([]) do
    child_processes = [ worker(MyStack.Server, []) ]
    supervise child_processes, strategy: :one_for_one
  end
end

defmodule MyStack.Stash do
  use GenServer

  # API

  def start_link(current_stack) do
    {:ok, _pid} = GenServer.start_link(__MODULE__, current_stack, name: __MODULE__)
  end

  def save_stack(new_stack) do
    GenServer.cast(__MODULE__, {:save_stack, new_stack})
  end

  def get_stack() do
    GenServer.call(__MODULE__, :get_stack)
  end

  # Implementation

  def handle_call(:get_stack, _from, current_stack) do
    {:reply, current_stack, current_stack}
  end

  def handle_cast({:save_stack, new_stack}, _current_stack) do
    {:noreply, new_stack}
  end
end

defmodule MyStack.Server do
  use GenServer

  # External API

  def start_link() do
    {:ok, _pid} = GenServer.start_link(__MODULE__, [], name: __MODULE__)
  end

  def pop do
    GenServer.call(__MODULE__, :pop)
  end

  def push(item) do
    GenServer.cast(__MODULE__, {:push, item})
  end

  # GenServer API

  def init([]) do
    stack = MyStack.Stash.get_stack()
    {:ok, stack}
  end

  def handle_call(:pop, _from, [h | t]) do
    {:reply, h, t}
  end

  def handle_cast({:push, item}, stack) do
    {:noreply, [item | stack]}
  end

  def terminate(_reason, stack) do
    MyStack.Stash.save_stack(stack)
  end
end

```
