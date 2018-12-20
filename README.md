# Leetcode

##Question One ReverseString

1. 
#### Can solve using let... of ES6 syntax, the key point is `reversed = char + reversed`:the previous value is added after the char of each string; The same thing we can do withthe ascending for loop statement. 
 ```
 function reverseStr(str) {
    if (str) {
        let reversed = '';
        for (let character of str) {
            reversed = character + reversed; 
        }
        return reversed; 
    }
    return null;
}
```
2. 
#### Sovling using destructuring assignment to swap is a clever method too. 
```
function reverseStr(str) {
    if (str) {
        let arr = str.split('');
        for (let left = 0, right = arr.length -1; left < right; left++, right --) {
            // destructuring assignment
            [arr[left], arr[right]] = [arr[right], arr[left]];
        }
        return arr.join('');

    }
    return null;
}
```
3. 
#### Solving using reduce method
```
function reverse(str) {
    if (str) {
        return str.split('').reduce((accumulator, currentValue) => {
            return currentValue + accumulator;
        }, '');
    }
    return null;
}
```

