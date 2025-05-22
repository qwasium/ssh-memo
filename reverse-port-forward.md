## `-R` (reverse shell etc.)

`-R` (remote port forwarding).
See `man ssh` for more details.

Create SSh tunnel to forward: **host port** -> **client port**

This is reversed connection so the connection is a 2-step precess.

1. **client** -> **host**
2. **host** -> **client**.

### Cheatsheet

1. From client: `ssh -R <host port>:localhost:<client port> <host user>@<host address>`
2. From host: `ssh <client user>@localhost -p <server port>`
