SSH help examples
=================

Simply if you want to open connection to some server:
```
ssh <user>@host [-p<port>]
```
Examples:
```
ssh root@8.8.8.8
ssh user@187.56.42.34 -p1084
```
If you want to use some special key file:
```
ssh -i key.pem root@10.0.4.2
```

To allow remote server connect to your machine:
```
ssh -R <port_at_remote>:<access_host>:<access_port> <user>@<remote_host>
```
It means that you will connect to <remote_host> by <user> and open server on <port_at_remote>
and when some app from some app from server try to access to this port then it will
get <access_host>:<access_port>

Another way, when you want to connect to some app that is behind NAT on remote server,
or allow only localhost connections:
```
ssh -L <local_port>:<access_host>:<access_port> <user>@<remote_host>
```
When you open localhost:<local_port> and get access to <access_hots>:<access_port>

And at last you can upload file to remote host:
```
scp -P<port> <user>@<host>:<remote_path> <local_path> # download
scp -P<port> <local_path> <user>@<host>:<remote_path> # upload
```
