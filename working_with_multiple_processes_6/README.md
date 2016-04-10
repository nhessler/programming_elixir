Exercise WorkingWithMultipleProcesses-6
=======================================

### Question

In the **pmap** code, I assigned the value of **self** to the variable **me** at the top of the method and then used **me** as the target of the message returned by the spawned processes. Why use a separate variable here?


### Answer

because the function that me is used in is run on a separate process so **self** would be different. this allows the function to have access to the main process id so it knows where to send the message back to when it's calculated.
