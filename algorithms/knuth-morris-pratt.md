## Knuth Morris Pratt \(KMP\) Algorithm

A string matching algorithm wants to find the starting index`m`in string`S[]`that matches the search word`W[]`.

**Longest Suffix Prefix table**

```js
function createLSPTable(pattern) {
    let table = [0]; // base case
    for (let i = 0; i < pattern.length; i++) {
        let j = table[i-1]; // take previous value
        while (j > 0 && pattern[i] === pattern[j]) {
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

**Search**

```js
function search(pattern, text) {
    // base case
    if (pattern.length === 0) {
        return 0
    }
    
    let lsp = createLSPTable(pattern);
    let j = 0;
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



