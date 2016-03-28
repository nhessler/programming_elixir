Exercise ModulesAndFunctions-7
==============================

### Question

Find the library functions to do the following, and then use each in iex. (If the word *Elixir* or *Erlang* appears at the end of the challenge, then you’ll find the answer in that set of libraries.)

* Convert a float to a string with two decimal digits. (Erlang)
* Get the value of an operating-system environment variable. (Elixir)
* Return the extension component of a file name (so return `.exs` if given `"dave/test.exs"`). (Elixir)
* Return the process’s current working directory. (Elixir)
* Convert a string containing JSON into Elixir data structures. (Just find; don’t install.)
* Execute a command in your operating system’s shell.


### Answer

```elixir

# Convert a float to a string with two decimal digits. (Erlang)
:io.format("~.2f~n", [2.0/2.0]) #=> 1.00

# Get the value of an operating-system environment variable. (Elixir)
System.get_env["Home"] #=> "/Users/nathan/"

# Return the extension component of a file name (so return .exs if given "dave/test.exs"). (Elixir)
Path.extname("basename.ext") #=> ".ext"

# Return the process’s current working directory. (Elixir)
System.cwd() #=> "/Users/nathan"

# Convert a string containing JSON into Elixir data structures. (Just find; don’t install.)
# https://github.com/cblage/elixir-json
json_input = "{\"key\":\"this will be a value\"}"
{status, list} = JSON.decode(json_input) #=> {:ok, %{"key" => "this will be a value"}}

# Execute a command in your operating system’s shell.”
System.cmd "echo", ["hello"] #=> {"hello\n", 0}

```
