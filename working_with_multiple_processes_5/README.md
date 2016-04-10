Exercise WorkingWithMultipleProcesses-5
=======================================

### Question

Repeat the two, changing **spawn_link** to **spawn_monitor**.


### Answer

exiting and raising resulted in what we would have expected. A ":DOWN" message instead of an ":EXIT" message but everything else was the same.

```elixir

defmodule MultiProc do

  def self_exit(origin) do
    send origin, "This process will self exit"
    exit(:boom)
  end

  def run_exit do
    Process.flag(:trap_exit, true)
    pid = spawn_monitor(MultiProc, :self_exit, [self])
    :timer.sleep 5000
    check_messages
  end

  def check_messages do
    receive do
      msg ->
        IO.puts inspect(msg)
        check_messages
    after 1000 ->
        IO.puts "Done"
    end
  end

  def self_raise(origin) do
    send origin, "This process will self raise"
    raise "this is my purpose"
  end

  def run_raise do
    Process.flag(:trap_exit, true)
    pid = spawn_monitor(MultiProc, :self_raise, [self])
    :timer.sleep 5000
    check_messages
  end
end

```
