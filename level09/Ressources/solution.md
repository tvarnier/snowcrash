## FLAG: `25749xKZ8L7DkSCwJkT9dyv6f`

> cat token
```
    f4kmm6p|=�p�n��DB�Du{��
```

> ./level09 token
```
    tpmhr
```
> ./level09 aaaaaaa
```
    abcdefg
```
> ./level09 abcdefg
```
    acegikm
```

## This program takes a string and add its index to each char
## `token` content must be the real token taken trough this program
## We'll create a script which does the opposite

> vi /tmp/09_reverse.py
```
#!/usr/bin/python
import sys
i = 0
tokenfile = open("/home/user/level09/token")
for c in tokenfile.readlines()[0]:
    if ord(c) - i <= 0:
        break
    sys.stdout.write(chr(ord(c) - i))
    i += 1
print("\n")
```

> python /tmp/09_reverse.py token
```
    f3iji1ju5yuevaus41q1afiuq
```

> su flag09
> getflag
```
    Check flag.Here is your token : s5cAJpM8ev6XHw998pRWG728z
```