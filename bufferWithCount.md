```js
import Most from "most";
import {add, append, curry, takeLast} from "ramda";

// Number -> Stream a -> Stream [a]
let buffer = curry((n, s$) => {
  return s$
    .loop((memo, item) => {
      let value = takeLast(n, append(item, memo));
      let seed = value.length == n ? [] : value;
      return {seed, value};
    }, [])
    .filter(x => x.length == n)
});

let s$ = Most
  .periodic(100, 1)
  .scan(add, 0); // 0--1--2--...

buffer(3, s$) // [0, 1, 2]--[3, 4, 5]--...
  .observe(console.log); 
```
