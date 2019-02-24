AWK examples
============

Awk is very usefull for read logs and any table data CSV for example:
```
ps ax | grep <process_name> | grep -v grep | awk '{print $1}' # returns PID of some process or PIDS
```
*Attention*: there is single apostroph not double!
