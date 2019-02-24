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
