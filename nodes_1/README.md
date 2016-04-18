Exercise Nodes-1
================

### Question
Set up two terminal windows, and go to a different directory in each. Then start up a named node in each. In one window, write a function that lists the contents of the current directory.

``` elixir

​fun = ​fn​ -> IO.puts(Enum.join(File.ls!, ​"​​,"​)) ​end​

```

Run it twice, once on each node.”


### Answer

**node-one** posted the list of files in the directory it was started in and put them in **node-one**'s screen. **node-two** posted the list of files in the directory it was started in but put them in **node-one**'s screen
