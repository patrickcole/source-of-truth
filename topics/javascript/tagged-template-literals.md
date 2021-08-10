# Tagged Template Literals

```js
const name = "Patrick";

function taggingThis(strings, ...vals) {
  return strings[0] + vals[0] + strings[1];
}

console.log(taggingThis`Hey!!, I'm ${name} !!`);
// => "Hey!!, I'm Patrick !!";

// Debugging:
// strings[0] -> "Hey!!, I'm ";
// strings[1] -> " !!";
// vals[0] -> "Patrick"

```

-----

## Sources

- [11+ JavaScript Features You’ve Probably Never Used](https://blog.bitsrc.io/features-of-javascript-you-probably-never-used-4c117ba3f025)
