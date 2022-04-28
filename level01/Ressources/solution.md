## FLAG : `x24ti5gi3x0ol2eh4esiuxias`

## Still nothing in home
> ls -la
```
    total 12
    dr-x------ 1 level01 level01  100 Mar  5  2016 .
    d--x--x--x 1 root    users    340 Aug 30  2015 ..
    -r-x------ 1 level01 level01  220 Apr  3  2012 .bash_logout
    -r-x------ 1 level01 level01 3518 Aug 30  2015 .bashrc
    -r-x------ 1 level01 level01  675 Apr  3  2012 .profile
```

## But there something suspicious in /etc/passwd
```
    ...
    flag01:42hDRfypTqqnw:3001:3001::/home/flag/flag01:/bin/bash
    ...
```
## Second field `42hDRfypTqqnw` is the hash of flag01's password

------------------------------------------------

## We'll use `John The Ripper` to dehash this

## John need the `/etc/passwd` file
## We import this to our mahine
> scp -P 4242 level01@127.0.0.1:/etc/passwd .

## And put it Through john
> john --show passwd
> ~/42/john-1.9.0/run/john --show passwd
```
flag01:abcdefg:3001:3001::/home/flag/flag01:/bin/bash

1 password hash cracked, 0 left
```
## The password for flag01 is `abcdefg`

------------------------------------------------

> su flag01
> getflag
```
    Check flag.Here is your token : f2av5il02puano7naaf6adaaf
```