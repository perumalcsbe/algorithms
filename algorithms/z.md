**Z algorithm**

is a linear time string matching algorithm which runs in **O\(n\)** complexity. It is used to find all occurrence of a pattern **P **in a string **S**, which is common string searching problem.

Def. Zi\(P\) = the length of the longest substring of P that starts at i &gt; 1 and matches a prefix of P.

```
P = “aardvark”: Z2 = 1, Z6 = 1
P = “alfalfa”: Z4 = 4
P = “photophosphorescent”: Z6 = Z10 = 3
```



