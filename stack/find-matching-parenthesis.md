## Find closing/opening parenthesis

`String.prototype.findParenMatch = function(pos)`an index`Int pos`.

Based on the given index, return the matching parenthesis in the given string.

### What is the matching parenthesis?

Consider this string:`(())`

The two outer parenthesees are a set, and the two inner ones are another set

```
   Set 1
  ________
 |        |
 V        V
 
(  (  )  )

    ^  ^
    |__|
    Set 2

```

So for the following string:

```
str = "(something)"
str.findParenMatch(0) 
// returns 10 because the parenthesis that matches the one on index 0 is at index 10.
```

Similarly,

```
str = "(something)"
str.findParenMatch(10) 
// returns 0 because the parenthesis that matches the one on index 10 is at index 0.
```

Lets consider something a bit more complicated:

```
str = "(som(th)ng)"
str.findParenMatch(0) 
// returns 10 because the parenthesis that matches the one on index 0 is at index 10.

str.findParenMatch(10) 
// returns 0 because the parenthesis that matches the one on index 10 is at index 0.

str.findParenMatch(4) 
// returns 7 because the parenthesis that matches the one on index 4 is at index 7.

str.findParenMatch(7) 
// returns 4 because the parenthesis that matches the one on index 7 is at index 4.
```

More cases:

```
str = ")()"
str.findParenMatch(0) 
// returns -1 because there is no matching parenthesis in the string

str.findParenMatch(1) 
// returns 2 as usual.
```

Even more:

```
str = "())"
str.findParenMatch(0) 
// returns 1 since it's the closest match

str.findParenMatch(1) 
// returns 0 as usual.

str.findParenMatch(2) 
// returns -1 because it's already closed by the parenthesis at index 1.
```

### Input Assumptions {#input-assumptions}

The index`pos`/`n`provided will always be within the range of the string itself.

The only characters occurring in the string are`a-z`and`()`- you do**not**need to account for other types of brackets such as`[]`or`{}`.

```js
String.prototype.findParenMatch = function(pos) {
  let res = pos;
  let count = 0;
  // open parathesis
  if (this[pos] === ')') {
  
    while (res >= 0) {
      if (this[res] === '(') {
        count--;
        if (count == 0) {
          return res;
        }
      }
      
      if (this[res] === ')') {
        count++;
      }
      res--;
    }
    
  }
  // close paranthesis
  if (this[pos] === '(') {
  
    while (res < this.length) {
      if (this[res] === ')') {
        count--;
        if (count == 0) {
          return res;
        }
      }
      
      if (this[res] === '(') {
        count++;
      }
      res++;
    }
  }
  
  return -1;
};
```



