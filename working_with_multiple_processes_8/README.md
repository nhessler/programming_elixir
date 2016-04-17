Exercise WorkingWithMultipleProcesses-8
=======================================

### Question

Run the Fibonacci code on your machine. Do you get comparable timings? If your machine has multiple cores and/or processors, do you see improvements in the timing as we increase the application’s concurrency?


### Answer

seems like things decreased on 2 processes and 3 processes. But, things leveled out until we got to 6 processes where it then decreased again and leveled out for the remaining numbers. I assume there is something special happening at the OS/hardware level for 6 since I only have 2 cores.

```

[{37, 24157817}, {37, 24157817}, {37, 24157817}, {37, 24157817}, {37, 24157817}, {37, 24157817}]

 #   time (s)
 1     9.59
 2     5.08
 3     4.18
 4     4.29
 5     4.43
 6     3.76
 7     3.73
 8     3.67
 9     3.67
10     3.74

```
