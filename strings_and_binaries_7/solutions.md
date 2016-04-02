Exercise StringsAndBinaries-7
=============================

### Question

Chapter 7, ​*Lists and Recursion*​, had an exercise about calculating sales tax. We now have the sales information in a file of comma-separated **id**, **ship_to**, and **amount** values. The file looks like this:

```

id,ship_to,net_amount
123,:NC,100.00
124,:OK,35.50
125,:TX,24.00
126,:TX,44.80
127,:NC,25.00
128,:MA,10.00
129,:CA,102.00
120,:NC,50.00

```

Write a function that reads and parses this file and then passes the result to the **sales_tax** function. Remember that the data should be formatted into a keyword list, and that the fields need to be the correct types (so the **id** field is an integer, and so on).

You’ll need the library functions **File.open**, **IO.read(file, :line)**, and **IO.stream(file)**.


### Answer

```elixir

defmodule Order do

  def read_orders(filename) do
    {:ok, file} = File.open(filename, [:read, :utf8])
    headers = _build_headers(IO.read(file, :line))
    orders = Enum.map(IO.stream(file, :line), &(_build_order(&1, headers)))
    File.close(file)

    orders
  end

  defp _build_order(line, headers) do
    line
      |> _get_parts
      |> _cast_values(headers)
  end

  defp _build_headers(line) do
    line
      |> _get_parts
      |> Enum.map(&(String.to_atom(&1)))
  end

  defp _cast_values(values, types) do
    values
      |> Enum.zip(types)
      |> Enum.map(&(_cast_value(&1)))
  end

  defp _cast_value({value, :id}), do: {:id, String.to_integer(value)}
  defp _cast_value({value, :ship_to}), do: {:ship_to, String.to_atom(value)}
  defp _cast_value({value, :net_amount}), do: {:net_amount, String.to_float(value)}

  defp _get_parts(line) do
    line
      |> String.strip
      |> String.split(",")
  end

end

```
