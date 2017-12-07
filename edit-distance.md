Given two words _word1 _and _word2_, find the minimum number of steps required to convert word1 to word2. \(each operation is counted as 1 step.\)

You have the following 3 operations permitted on a word:

* Insert a character
* Delete a character
* Replace a character

**Example**

Given word1 =`"mart"`and word2 =`"karma"`, return`3`.



| operations | insert | delete | replace |
| :--- | :--- | :--- | :--- |
| i = 4 { w2.len &gt; w1.len} | 1 + "a" =&gt; "marta" |  |  |
| i = 3  |  |  | 1 + "t -&gt; m" =&gt; :"marma" |
| i = 2 |  |  |  |
| i = 1 |  |  |  |
| i = 0 |  |  | 1 + "m-&gt;k" =&gt; :"karma" |
|  |  |  |  |



