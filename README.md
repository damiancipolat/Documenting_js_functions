<img src="https://github.com/damiancipolat/Functional_programming_in_JS/blob/master/doc/fp.png?raw=true" width="125px" align="right" />

# Documenting functions in javascript
The idea of this repository is to continue with the last 2 projects that I raised on functional programming in js.

## Why?
For some time I have been dedicated to javascript and I see that there is still no standard on how developers should document what data should be passed as parameters. Although JS is not a typed language, somehow we have to specify what data is sent in each parameter.

## Solution - Type Signatures
These type notations are a **meta language** called Type Signatures, defines the inputs and outputs for the function, sometimes including the number of arguments, the types of arguments and order of arguments contained by a function.

Type Signatures are based on Hindley-Milner Type system as a standard type system which is also followed by ML-influenced languages, including Haskell.

**Notation - examples**
```js

// length :: String → Number
const length = s => s.length;

// length :: [Number] → Number
const length = arr => arr.length;

// join :: (String, [String]) → String
const join = (separator, arr) => arr.join(separator)
```

Readings:
https://medium.com/hackernoon/function-type-signatures-in-javascript-5c698c1e9801
