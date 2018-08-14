# unexpected-token.  (syntax error)

When JavaScript engine can't parse the file because I made an error in my code.  It cannot even make it past the creation phase.  

More specifically, I started something I didn't finish.  Opened parenthesis I never closed, used an operator with no operand, ...

I first came across this error studying type coercion when I tried to typof the void operator.  

I expect this error will be a real pain becuase the message isn't very helpful.  It tells me there's something missing, but always tells me it's at the end of the file.
I'll have to go back through the WHOLE FILE to find where I made my mistake.

___

## Code where I first found the error

```js
typeof void

// comments
```

```js
typeof void;

// comments
```

These look so similar, but are soooo different.  With the semicolon JS catches the error before moving on to the rest of the file.
This way it can tell me the error is on line 1, instead of having to stumble to the end and tell me something unhelpful.

___

## The Fix

Well, void is an operator.  it requires a value to it's right, so i gave it one.

```js
typeof void null;
```

_null_ for fun, but it could be anything.  doesn't matter. _void_ turns anything to _undefined_.

___

## Messages from different runtimes

 * Google Chrome (V8 Engine)
 ```
unknown: Unexpected token (3:0)
  1 | // example 1
  2 | typeof void
> 3 | 
    | ^
    
  ```
 
 * Safari (WebKit Engine)
 ```
 unknown: Unexpected token (3:0)
  1 | // example 1
  2 | typeof void
> 3 | 
    | ^
 ```
  
 * Opera (Carakan Engine)
 ```
 unknown: Unexpected token (3:0)
  1 | // example 1
  2 | typeof void
> 3 | 
    | ^
 ```
 * Mozilla Firefox (SpiderMonkey Engine)
 ```
 unknown: Unexpected token (3:0)
  1 | // example 1
  2 | typeof void
> 3 | 
    | ^
 ```
___

## More instances
 
 ```js
  let var x;
 
 ```

 ```js
 const x;
 
 ```
Cannot declare a const without initialising it.

___

```js
 {} = [0];
```

Cannot assign an array to empty curly braces. I can only assign values to variables, objects... and {} is a value.
Conclusion: You cannot assign a value to a value

A way of correcting this:

```js
 var obj = {} = [0];
```
This method would override the issue and assign [0] to var obj. 


ongoing.  (almost) every time you come across it, copy-paste the code into this repo. if the code is long you can put it in a separate file.

[replit](https://repl.it/@colevandersWands/unexpected-token)

___

## helpful links

[the first result](https://airbrake.io/blog/javascript-error-handling/unexpected-token)

___

## review

I learned semicolons can help with debugging.

