Exercise Nodes-4
================

### Question

The ticker process in this chapter is a central server that sends events to registered clients. Reimplement this as a ring of clients. A client sends a tick to the next client in the ring. After 2 seconds, that client sends a tick to its next client. When thinking about how to add clients to the ring, remember to deal with the case where a client’s receive loop times out just as you’re adding a new process. What does this say about who has to be responsible for updating the links?


### Answer

``` elixir

defmodule RingTicker do

  @interval 2000 # 2 seconds
  @entrance :ring_entrance

  def start do
    spawn(__MODULE__, :enter, [:global.whereis_name(@entrance)])
  end

  def enter(:undefined) do
    :global.register_name(@entrance, self)
    tick(self)
  end

  def enter(entrance) do
    send entrance, {:insert, self}
    standby
  end

  def standby do
    receive do
      {:join, next_ticker} -> tock(next_ticker)
    end
  end

  def tock(next_ticker) do
    receive do
      {:tick} ->
        IO.puts "tock on #{inspect self}"
        tick(next_ticker)
    end
  end

  def tick(next_ticker) do
    receive do
      {:insert, new_ticker} ->
        send new_ticker, {:join, next_ticker}
        tick new_ticker
    after
      @interval ->
        IO.puts "tick on #{inspect self}"
        send next_ticker, {:tick}
        tock next_ticker
    end
  end
end

```
