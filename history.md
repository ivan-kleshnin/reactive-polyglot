### Track history for N events

#### RxJS

```js
let {append, drop, repeat} = require("ramda")

let appendSliding = curry((n, x, xs) => {
  let ys = append(x, xs)
  if (ys.length > n) {
    return drop(ys.length - n, ys)
  } else {
    return ys
  }
})

let history = function (n) {
  if (n <= 0) {
    throw Error("n must be an unsigned integer, got "+ String(n))
  }
  let put = appendSliding(n)
  return this.scan((stateHistory, newState) => {
    return put(newState, stateHistory)
  }, repeat(null, n - 1))
}

// Usage
statefulStream
  ::history(3)
```
