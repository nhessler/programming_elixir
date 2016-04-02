Exercise StringsAndBinaries-3
=============================

### Question

Try the following in iex:

```shell

​iex>​ [ ​'cat'​ | ​'dog'​ ]
['cat',100,111,103]

```

Why does iex print **’cat’** as a string, but **’dog’** as individual numbers?


### Answer

This happens because **'cat'** is not an individual character, but a character list so the whole array is not a list of characters. thus, **'cat'** gets printed as a string, but the array that **'cat'** is in does not
