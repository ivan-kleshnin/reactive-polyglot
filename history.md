```js
import Most from "most";
import {append, curry, drop, head, repeat, takeLast} from "ramda";

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
      olderState: head(takeLast(1, drop(2, x))),
      prevState: head(takeLast(1, drop(1, x))),
      currState: head(takeLast(1, x)),
    };
  })
  .observe(console.log);
```
