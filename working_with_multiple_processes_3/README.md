Exercise WorkingWithMultipleProcesses-3
=======================================

### Question

Use **spawn_link** to start a process, and have that process send a message to the parent and then exit immediately. Meanwhile, sleep for 500 ms in the parent, then receive as many messages as are waiting. Trace what you receive. Does it matter that you weren’t waiting for the notification from the child when it exited?


### Answer

It does not matter that we were not *receiving* messages at the time they were sent.

``` elixir

defmodule MultiProc do

  def self_exit(origin) do
    send origin, "This process will self exit"
    exit(:boom)
  end

  def run_exit do
    Process.flag(:trap_exit, true)
    pid = spawn_link(MultiProc, :self_exit, [self])
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
end

```
