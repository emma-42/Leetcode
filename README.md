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
4. 
#### Debugger Statements Steps:
```
     - Add a `Debugger` statement in your function;
     - Call the function manually;
     - At the terminal, run `node inspect index.js`;
     - To continue execution of the file, press `c` then enter;
     - To launch a 'repl' session, type `repl` then enter
     - To exit 'repl', press Ctrl + C; 
```
5. 
#### Regular Expression:non alphanumeric
```
/[^a-zA-Z0-9]/g
```
## Question Two Palindrome
1. 
#### Sovling using Array.prototype.every to compare every item in the array with the mirror side to see whether they are equal
```
function isPalindrome(str) {
    let arr = str.replace(/[^a-zA-Z0-9]/gi, '').toLowerCase().split('');
    let lastDigit = arr.length-1;
    return arr.every((curr, index) => curr === arr[lastDigit - index]);
}
```

## Question Three Reverse Integer
1. 
#### Math.sign() returns the sign of a number, indicating whether the number is positive, negative or zero. This function has 5 kinds of return values, 1, -1, 0, -0, NaN, which represent 'positive number', 'negative number', 'positive zero', 'negative zero' and NaN respectively.
2. 
#### The key is to convert int to string and reverse it. 
```
function reverseInt(n) {
    let reversed = parseInt(n.toString().split('').reverse().join(''));
    if (reversed >= Math.pow(2, 31) | reversed <= Math.pow(-2, 31) - 1) {
        return 0;
    } else {
        return reversed * Math.sign(n);
    }
}
```
3. 
#### floor() is extremely slow on all platforms since it has to implement a lot of behaviour from the IEEE fp spec. You can't really use it in inner loops.
4. 
#### Sovling using mod. But keep in mind that n = n / 10 in JavaScript can be decimal point. Which first I thought of Math.round(), which is incorrect, later I thought of Math.floor(), it works but time is really slow and should aviod it in the for loop. So I am using parseInt() to solve the problem.
```
function reverseInt(x) {
    let reversed = 0;
    while (x) {
        reversed = reversed * 10 + x % 10;
        x = parseInt(x / 10); 
    }
    if (reversed >= Math.pow(2, 31) || reversed <= Math.pow(-2, 31) - 1) {
        return 0;
    } else {
        return reversed
       
    }
};
```
5. ****
[Does Javascript handle integer overflow and underflow? If yes, how?](https://stackoverflow.com/questions/19054891/does-javascript-handle-integer-overflow-and-underflow-if-yes-how)
****


