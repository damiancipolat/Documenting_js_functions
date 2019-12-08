<img src="https://github.com/damiancipolat/Functional_programming_in_JS/blob/master/doc/fp.png?raw=true" width="125px" align="right" />

# Documenting functions in javascript
The idea of this repository is to continue with the last 2 projects that I raised on functional programming in js.

## But why?
For some time I have been dedicated to javascript and I see that there is still no standard on how developers should document what data should be passed as parameters. Although JS is not a typed language, somehow we have to specify what data is sent in each parameter.

**Currently:** Currently this is one of my functions, I have started working with this format.

```js
/*
  Receive currency code and return money simbol.
  Params
    currency : string
  Return
    string
*/
const getSymbol = (currency)=>{

  switch(currency){
    case 'ARS':
      return '$';
    case 'USD':
      return 'U$S';
    default:
      return '$';
  }
  
}
```

**New format:** I'm moving to this new format.

```js
/*
  Receive currency code and return money simbol.
  getSymbol:: string → string
*/
const getSymbol = (currency)=>{...}
```

## Solution - Type Signatures
These type notations are a **meta language** called Type Signatures, defines the inputs and outputs for the function, sometimes including the number of arguments, the types of arguments and order of arguments contained by a function.

Type Signatures are based on Hindley-Milner Type system as a standard type system which is also followed by ML-influenced languages, including Haskell.

**Some examples:**
```js
// length :: String → Number
const length = s => s.length;

// length :: [Number] → Number
const length = arr => arr.length;

// join :: (String, [String]) → String
const join = (separator, arr) => arr.join(separator)
```

## Code examples:
The sections are divided in **One parameter** / **Multiple parameters** / **High order functions**.

### One parameter:
Examples using 1 parameter as input and one flat return data, **f(x) = y**.

- STRING - f(String) = Number:
```js
//length :: String → Number
const length = (a)=>a.length;
```

- NUMBER - f(Number) = Number:
```js
//increase :: Number → Number
const increase = value => value+10;
```

- BOOLEAN - f(Bool) = Bool.
```js
//inverse :: Bool → Bool
const inverse = value => !value;
```

- ARRAY - f([x]) = Number.
```js
//length :: [a] → Number
const length = list => list.length;

//length :: [string] → Number
const length = list => list.length;

//length :: [Number] → Number
const length = list => list.length;
```

- DATE - f(date) = Bool.
```js
//expire :: Date → Bool
const expire = expireDate => new Date()<=expireDate;
```

- FUNCTION - f(g([a])) = [b].
```js
//map :: (a → b) → [a] → [b]
const map = fn => arr => arr.map(fn)
```

- ANY - f(*) = b.
```js
//isNull :: * → Bool.
const isNull = obj => !!obj;
```

- OBJECT - f(object) = String.

**Generic format**
```js
//map :: object → string
const toJson = obj => JSON.stringify(obj);
```

**Custom format**
```js
//map :: {name:String, age: Number} → string
const toJson = people => JSON.stringify(people);
```

**Array of objects**
```js
//map :: [{name:String, age: Number}] → [string]
const encode = people => people.map(p=>btoa(p));
```

### Multiple parameters:
Examples using 2 parameters as input and one flat return data, **f(x,y) = z**.

- STRING:
```js
// join :: (String, [String]) → String
const join = (separator, arr) => arr.join(separator)
```

- Number - f(x,y) ) = z.
```js
// sum :: (Number, Number) → Number
const sum = (x,y) => x+y;
```

- Array - f([a],b) = c.
```js
//concat :: [*],string → string
const concat = (list,char) => list.join(char).
```

### High order parameters:
When a function is passed as parameter, we wrap it’s signature in a parentheses to present a more meaningful overall Type Signature. f(g(x)) = y

```js
// addOneToAll :: ((Number → Number),[Number]) → [Number]
const addOneToAll = (addOne = x=>x+1 , arr) => arr.map(addOne)
```

## Readings:
- https://medium.com/hackernoon/function-type-signatures-in-javascript-5c698c1e9801
- https://github.com/ramda/ramda/wiki/Type-Signatures
- https://ramdajs.com/docs/
