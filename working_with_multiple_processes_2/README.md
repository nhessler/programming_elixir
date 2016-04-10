Exercise WorkingWithMultipleProcesses-2
=======================================

### Question

Write a program that spawns two processes and then passes each a unique token (for example, “fred” and “betty”). Have them send the tokens back.

* Is the order in which the replies are received deterministic in theory? In practice?
* If either answer is no, how could you make it so?


### Answer

``` elixir

defmodule Deterministic do
  def echo do
    receive do
      {sender, msg} -> send sender, msg
    end
  end

  def run do
    p1 = spawn(Deterministic, :echo, [])
    p2 = spawn(Deterministic, :echo, [])

    send p1, {self, "first message"}
    send p2, {self, "second message"}

    receive do
      msg -> IO.puts msg
    end

    receive do
      msg -> IO.puts msg
    end

  end
end

```

* It should not be deterministic in theory, but has been so far in practice
* You could add pattern matching in each receive to guarantee order
