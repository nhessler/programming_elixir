Exercise Nodes-2
================

### Question

When I introduced the interval server, I said it sent a tick “about every 2 seconds.” But in the receive loop, it has an explicit timeout of 2,000 ms. Why did I say “about” when it looks as if the time should be pretty accurate?


### Answer

every time `Ticker` gets a `{:receive, pid}` the countdown is reset.
