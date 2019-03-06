SED examples
============

Sed is usefull for replace something
```
sed -i -e 's/few/asd/g' hello.txt
```
-i mean replace *i*n place\
-e option indicates the *e*xpression/command to run, in this case\
s - means replace *s*tring\
g - means *g*lobal\


Trim leading whitespaces and tabulations in file.txt:

```sed 's/^[ \t]*//' file.txt```

Trim trailing whitespaces and tabulations in file.txt:

```sed 's/[ \t]*$//' file.txt```

Trim leading and trailing whitespaces and tabulations in file.txt:

```sed 's/^[ \t]*//;s/[ \t]*$//' file.txt```

Delete blank lines in file.txt:

```sed '/^$/d' file.txt```
