AWK examples
============

Awk is very usefull for read logs and any table data CSV for example:
```
ps ax | grep <process_name> | grep -v grep | awk '{print $1}' # returns PID of some process or PIDS
```
*Attention*: there is single apostroph not double!

If we find hello on stdin then print whole line, it is case sensetive

```awk '/hello/{print $0}'```

Show line having length > 50 using action

```awk '{ if (length($0) > 50) print }' <file>```

Show, for each row, ROW Number FIELD Number

```awk 'NF > 0 { print NR,FNR,NF }' <file>```

Set Output Field Separator

```awk 'BEGIN { OFS="->"} { print $1,$2,$3,$4 }' <file>```

Set Output Record Separator

```awk 'BEGIN { ORS="|\n"} { print $0 }' <file>```

Script can contain many blocks:
```
BEGIN {
  print "# Very Simple AWK Examples"
}
/#!\/bin\/bash/ { next }
/^# [0-9]*\./ {
  if (NOT_FIRST)
    print "```"
  else
    NOT_FIRST = 1
  $1 = "##"
  print
  print "```"
  next
}
{
  sub(/^# /,"",$0)
  print
}
END {
  print "```"
}
```
