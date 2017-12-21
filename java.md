Integer MIN & MAX values

```java
// min value
Integer.MIN_VALUE
// max value
Integer.MAX_VALUE
```

**char\[\]**

```java
char[] a = "test".toCharArray(); // ['t', 'e', 's', 't']
// length
a.length; // => 4
```

Lower & Upper cases

[http://www.asciitable.com/](http://www.asciitable.com/)

```java
// Lower case

// Using Character 
Character.isLowerCase('a'); // true
Character.isLowerCase('A'); // false
// Using ASCII
char ch = 'a';
(ch > 64 ) && (ch < 91); // true

// Upper case
Character.isUpperCase('B'); // true
Character.isUpperCase('b'); // false

char ch = 'A';
(ch > 96 ) && (ch < 123); // true
```

Collections

```java
ArrayList<List<Integer>> res = new ArrayList<List<Integer>>();
List<List<Integer>> res = new LinkedList<>();
// To add list to list
res.add(Arrays.asList(item1, item2..itemN));



//Sorting array
Arrays.sort(nums);
```



