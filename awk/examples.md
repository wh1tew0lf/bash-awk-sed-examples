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

Extract fields 2, 4, and 5 from file.txt:

```awk '{print $2,$4,$5}' <file>```

Count number of columns in file.txt:

```awk '{print NF; exit}' <file>```

Print each line where the 5th field is equal to ‘abc123’:

```awk '$5 == "abc123"' <file>```

Print each line where the 5th field is not equal to ‘abc123’:

```awk '$5 != "abc123"' <file>```

Print each line whose 7th field matches the regular expression:

```awk '$7  ~ /^[a-f]/' <file>```

Print each line whose 7th field does not match the regular expression:

```awk '$7 !~ /^[a-f]/' <file>```

Display a block of text with AWK

```awk ‘/start_pattern/,/stop_pattern/’ <file>```

Get unique entries in file.txt based on column 2 (takes only the first instance):

```awk '!arr[$2]++' <file>```

Remove duplicate entries in a file, without sorting:

```awk ‘!x[$0]++’ <file>```

Print rows where column 3 is larger than column 5 in file.txt:

```awk '$3>$5' <file>```

'Unpivot' file.csv data. Second column delimited by |, create one row per value; insert new values from column 2 to the end (column 5).

```awk '{n=split($2,s,"|");for (i=1;i<=n;i++) {$5=s[i];print}}' <file>```

Sum column 1 of file.txt:

```awk '{sum+=$1} END {print sum}' <file>```

Compute the mean of column 2:

```awk '{x+=$2}END{print x/NR}' <file>```

Given a file with data in the format of column 1 data|column 2 data, print out data so it is in the form of ("column 1","column 2")

```awk 'BEGIN {FS="|"}; { printf(" (\"%s\",\"%s\"),", $1, $2 ); }' < <file>```
