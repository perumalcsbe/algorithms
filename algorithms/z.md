**Z algorithm**

is a linear time string matching algorithm which runs in **O\(n\)** complexity. It is used to find all occurrence of a pattern **P **in a string **S**, which is common string searching problem.

Def. Zi\(P\) = the length of the longest substring of P that starts at i &gt; 1 and matches a prefix of P.

P = “a**a**rdv**a**rk”: Z2 = 1, Z6 = 1

P = “alf**alfa**”: Z4 = 4

P = “photo**pho**s**pho**rescent”: Z6 = Z10 = 3



```
S = ddddabacabssss
P = a b a c a b
Z = 6 0101 
```

| index | 0 | 1 | 2 | 3 | 4 | 5 |
| :--- | :---: | :--- | :--- | :--- | :---: | :---: |
| Character | a | b | a | c | a | b |
| Z-value | 6 \(length\) | 0 | 1 | 0 | 2 | 0 |
| how to | 0-5=&gt; 6 | 1-5 |  |  | 4-5=&gt;0-1 | 5-5 |



