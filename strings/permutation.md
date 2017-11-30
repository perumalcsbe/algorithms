```js
function permute(prefix, suffix, result) {
  if (suffix.length === 0) {
    result.push(prefix);
    return;
  } else {
    for(let i = 0; i < suffix.length; i++) {
      permute(prefix + suffix.charAt(i), suffix.substring(0, i) + suffix.substring(i+1), result);
    }
  }  
}


function permuation(str) {
  let result = [];
  permute('', str, result);
  return result;
}
```



