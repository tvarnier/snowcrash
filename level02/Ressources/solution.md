## FLAG : `f2av5il02puano7naaf6adaaf`

> ls
```
    level02.pcap
```
## `.pcap` is an application programming interface (API) for capturing network traffic
## We can use `tshark` to analyze its content

------------------------------------------------

## We import the level02.pcap file
> scp -P 4242 level02@127.0.0.1:/home/user/level02/level02.pcap .

## Change permissions to level02.pcap
> chmod 777 level02.pcap

## And give it to tshark
> tshark -r level02.pcap
## `-x` to print packets
> tshark -r level02.pcap -x
## mmm, It doesn't help

## We can use `-z` and some filter
> tshark -r level02.pcap -z follow,tcp,ascii,0
## We can read `Password: ft_wandr...NDRel.L0L`
## but `.` are non-printable characters

## We'll take the data in hexadecimal
> tshark -r level02.pcap -z follow,tcp,raw,0
## And convert it to string
[https://onlinestringtools.com/convert-hexadecimal-to-string]
```
    ...
    Password: ft_wandrNDRelL0L
    ...
```

## `ft_wandrNDRelL0L` -> `ft_waNDReL0L`

------------------------------------------------

> su flag02
> getflag
```
    Check flag.Here is your token : kooda2puivaav1idi4f57q8iq
```
