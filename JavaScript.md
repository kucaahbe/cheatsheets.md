# Javascript

### Get values from an object

```javascript
Object.values()
```

(does not have wide browser support yet)

### Get keys from an object

```javascript
Object.keys()
```

check the key presence in an object:

```javascript
const a = { key: 1 }
'not-present' in a // false
'key' in a // true
```

best conditional assignment:

```javascript
;(function (smth) {
  if ( 'key' in smth ) return;

  smth.key = {
    // do your stuff
  }
})('smth' in window && window.smth || (window.smth = {}))
```

### Binary to decimal:

```javascript
parseInt('011',2)
```

### Decimal to binary

```javascript
(4).toString(2)
```

### Get char code:

```javascript
"a".charCodeAt(0) // 97
```

### Get char by code:

```javascript
String.fromCharCode(97); // 'a'
```

### extend console.log

> [source](https://stackoverflow.com/a/26078207/692969)

```javascript
log = function() {
    const context = "My Descriptive Logger Prefix:";
    return Function.prototype.bind.call(console.log, console, context);
}() // <- !!!
```

### Semicolons:

[do not use them](https://mislav.net/2010/05/semicolons/)
semicolons mandatory:

```javascript
;(d + e).print() // line starts with parenthesis or square bracket
```
quote from the article:
> If you choose to omit semicolons where possible, my advice is to insert them immediately before the opening parenthesis or square bracket in any statement that begins with one of those tokens, or any which begins with one of the arithmetic operator tokens `/`, `+`, or `-` if you should happen to write such a statement.