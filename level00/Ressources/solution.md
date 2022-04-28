## Nothing in Home
> ls -la
```
    total 12
    dr-xr-x---+ 1 level00 level00  100 Mar  5  2016 .
    d--x--x--x  1 root    users    340 Aug 30  2015 ..
    -r-xr-x---+ 1 level00 level00  220 Apr  3  2012 .bash_logout
    -r-xr-x---+ 1 level00 level00 3518 Aug 30  2015 .bashrc
    -r-xr-x---+ 1 level00 level00  675 Apr  3  2012 .profile
```

## Looking for a file owned by `flag00`
> find / -user flag00 2>/dev/null
```
    /usr/sbin/john
    /rofs/usr/sbin/john
```

## This dumbass put his password in a readable file ...
> cat /usr/sbin/john
```
    cdiiddwpgswtgt
```

## It isn't, maybe not the dumbest person
> su flag00
```
    su: Authentication failure
```

## It's probably just encoded
[https://www.dcode.fr/cipher-identifier]
## IT IS !!! with Rot Cipher 13 Encodage
```
    nottoohardhere
```

------------------------------------------------

> su flag0
> getflag
```
    Check flag.Here is your token : x24ti5gi3x0ol2eh4esiuxias
```