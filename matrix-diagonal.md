```js
function diagonal(arr) {
  let res = [];
  let isUp = true;
  const n = arr.length;
  let i = 0;
  let j = 0;
  
  for (let k = 0; k < n*n;) {
    if (isUp) {
      for ( ; i >= 0 && j < n; j++, i--) {
           res.push(arr[i][j]);
           k++;
      }
 
      if (i < 0 && j <= n-1) {
        i = 0;
      }
      if (j == n) {
        i = i+2;
        j--;
      }
    } else {
      for ( ; j >= 0 && i < n; i++ , j--){
        res.push(arr[i][j]);
        k++;
      }
 
            
      if (j < 0 && i<=n-1) {
        j = 0;
      }
      if (i == n) {
        j = j + 2;
        i--;
      }
    }
    
    isUp = !isUp;
  }
 

  return res;
}
```



