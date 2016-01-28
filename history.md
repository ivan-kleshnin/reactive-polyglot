```js
import Most from "most";
import {append, curry, repeat} from "ramda";

// Number -> Stream a -> Stream [a]
let history = curry((n, s$) => {
  return s$
    .scan((states, nextState) => {
      return takeLast(n, append(nextState, states));
    }, repeat(n, null))
    .filter(x => x.length);
});

let most = Most
  .periodic(100, 1)
  .scan(add, 0); // 0--1--2--...

history(3, most) // [0]--[0, 1]--[0, 1, 2]--[1, 2, 3]--[2, 3, 4]--...
  .map(x => {
    return {
      olderState: x.slice(-3, x.length - 2, x)[0], // u--u--0--...
      prevState: x.slice(-2, x.length - 1, x)[0],  // u--0--1--...
      currState: x.slice(-1, x.length, x)[0],      // 0--1--2--...
    };
  })
  .observe(console.log);
```
