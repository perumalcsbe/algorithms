## Knuth Morris Pratt \(KMP\) Algorithm

A string matching algorithm wants to find the starting index`m`in string`S[]`that matches the search word`W[]`.

**Longest Suffix Prefix table**

```
 pattern = "ABCDABD"  
 text    = "ABC ABCDAB ABCDABCDABDE"

   pattern:  A  B  C  D  A  B  D
 LSP Table: [0]
     i = 1: [0, 0]      // j = 0  pattern[i] == pattern[j] ? j++ : j 
     i = 2: [0, 0, 0]
     i = 3: [0, 0, 0, 0]
     i = 4: [0, 0, 0, 0, 1] // j = 1
     i = 5: [0, 0, 0, 0, 1, 2] // j = 1  (j> 0 && B == B ? j = 1 + 1 => 2 
     i = 6: [0, 0, 0, 0, 1, 2, 3] // j = 2  (j> 0 && C != D ? j = 2
```

```js
function createLSPTable(pattern) {
    let table = [0]; // base case
    for (let i = 1; i < pattern.length; i++) {
        let j = table[i-1]; // take previous value
        while (j > 0 && pattern[i] !== pattern[j]) {
            j = table[j-1];
        }
        if (pattern[i] === pattern[j]) {
            j++;
        }
        table.push(j);
    }

    return table;
}
```

**Search Part**

```
LSP table [0, 0, 0, 0, 1, 2, 3]
          "ABC ABCDAB ABCDABCDABDE"
 j=0,i=0: "ABCDABD"                   j = 1 { A == A
 j=1,i=1:
```

```js
function search(pattern, text) {
    // base case
    if (pattern.length === 0) {
        return 0
    }

    let lsp = createLSPTable(pattern);
    let j = 0; // for pattern traversal
    // Traverse text
    for (let i = 0; i < text.length; i++) {
        while (j > 0 && text[i] !== pattern[j]) {
            j = lsp[j-1];
        }

        if (text[i] == pattern[j]) {
            j++;

            if (j === pattern.length) {
                return i-j-1;
            }
        }

    }  
    return -1; // no match found   
}
```



