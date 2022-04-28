## FLAG : `f2av5il02puano7naaf6adaaf`

> scp -P 4242 level02@127.0.0.1:/home/user/level02/level02.pcap .

## WireShark
> tshark -r level02.pcap
> tshark -r level02.pcap -x
> tshark -r level02.pcap -z follow,tcp,ascii,0  \* '.' are non printables
> tshark -r level02.pcap -z follow,tcp,raw,0    \* give hex

## convert hex to string
[https://onlinestringtools.com/convert-hexadecimal-to-string]
```
    ...
    Password: ft_wandrNDRelL0L
    ...
```

## `ft_wandrNDRelL0L` -> `ft_waNDReL0L`

> su flag02
> getflag
```
    Check flag.Here is your token : kooda2puivaav1idi4f57q8iq
```
