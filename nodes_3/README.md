Exercise Nodes-3
================

### Question

Alter the code so that successive ticks are sent to each registered client (so the first goes to the first client, the second to the next client, and so on). Once the last client receives a tick, the process starts back at the first. The solution should deal with new clients being added at any time.


### Answer

``` elixir

defmodule Ticker do

  @interval 2000    # 2 seconds
  @name     :ticker

  def start do
    pid =spawn(__MODULE__, :generator, [[]])
    :global.register_name(@name, pid)
  end

  def register(client_pid) do
    send :global.whereis_name(@name), {:register, client_pid}
  end

  def generator(clients) do
    receive do
      { :register, pid } ->
        IO.puts "registering #{inspect pid}"
        generator([pid | clients])
    after
      @interval ->
        IO.puts "tick"
        clients |> List.last |> notify_client
        clients |> rotate_clients |> generator
    end
  end

  defp notify_client(nil), do: nil
  defp notify_client(pid), do: send(pid, { :tick })

  defp rotate_clients([]), do: []
  defp rotate_clients(clients) do
    head = List.last(clients)
    tail = List.delete_at(clients, length(clients) - 1)
    [ head | tail ]
  end
end

defmodule Client do
  def start do
    pid = spawn(__MODULE__, :receiver, [])
    Ticker.register(pid)
  end

  def receiver do
    receive do
      { :tick } ->
        IO.puts "tock in client"
        receiver
    end
  end
end

```
