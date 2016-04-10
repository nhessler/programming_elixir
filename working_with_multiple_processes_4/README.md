Exercise WorkingWithMultipleProcesses-4
=======================================

### Question

Do the same, but have the child raise an exception. What difference do you see in the tracing?


### Answer

**raise** causes an error to be displayed outside of the message passing used by processes. But the Raised error, message, and error location were also added to the ":EXIT" message.

``` elixir

defmodule MultiProc do

  def self_raise(origin) do
    send origin, "This process will self raise"
    raise "this is my purpose"
  end

  def run_raise do
    Process.flag(:trap_exit, true)
    pid = spawn_link(MultiProc, :self_raise, [self])
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
