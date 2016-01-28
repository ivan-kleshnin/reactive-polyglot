# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

## Operators

Current ordering is subjective: from most common operators to less common.<br/>
Operator counterparts are not expected to be fully equivalent.<br/>
"Kinda the same" is the current definition.

### Create

Create stream from non-stream values.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>of / just</code></td><td><code>just</code></td></tr>
<tr><td><code>– (from)</code></td><td><code>of</code></td></tr>
<tr><td><code>from</code></td><td><code>from</code></td></tr>
<tr><td><code>fromEvent</code></td><td><code>fromEvent</code></td></tr>
<tr><td><code>fromPromise</code></td><td><code>fromPromise</code></td></tr>
<tr><td><code>periodic</code></td><td><code>interval + map</code></td></tr>
<tr><td><code>of + R.range</code></td><td><code>repeat</code></td></tr>
<tr><td><code>iterate</code></td><td><code>generate</code></td></tr>
<tr><td><code>generate</code></td><td><code>generate</code></td></tr>
</table>

### Map

Modify events one to one.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>map</code></td><td><code>map</code></td></tr>
<tr><td><code>constant</code></td><td><code>mapTo</code></td></tr>
<tr><td><code>delay</code></td><td><code>delay</code></td></tr>
<tr><td><code>timestamp</code></td><td><code>timestamp</code></td></tr>
</table>

### Transform

Modify events * to *.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>scan</code></td><td><code>scan</code></td></tr>
<tr><td><code>chain / flatMap</code></td><td><code>flatMap</code></td></tr>
<tr><td><code>concatMap</code></td><td><code>concatMap</code></td></tr>
<tr><td><code>join</code></td><td><code>mergeAll</code></td></tr>
<tr><td><code>loop</code></td><td><code>scan + map</code></td></tr>
</table>

### Filter

Skip events by predicate or signal.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>filter</code></td><td><code>filter</code></td></tr>
<tr><td><code>skipRepeats</code></td><td><code>distinctUntilChanged</code></td></tr>
<tr><td><code>skipRepeatsWith</code></td><td><code>– (scan)</code></td></tr>
<tr><td><code>skip</code></td><td><code>skip</code></td></tr>
<tr><td><code>take</code></td><td><code>take</code></td></tr>
<tr><td><code>slice</code></td><td><code>skip + take</code></td></tr>
<tr><td><code>skipWhile</code></td><td><code>skipWhile</code></td></tr>
<tr><td><code>takeWhile</code></td><td><code>takeWhile</code></td></tr>
<tr><td><code>since / skipUntil</code></td><td><code>skipUntil</code></td></tr>
<tr><td><code>until / takeUntil</code></td><td><code>takeUntil</code></td></tr>
<tr><td><code>during</code></td><td><code>window + take(1)</code></td></tr>
</table>

### Combine 

Combine multiple streams into single.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>merge</code></td><td><code>merge</code></td></tr>
<tr><td><code>combine</code></td><td><code>combineLatest</code></td></tr>
<tr><td><code>sample</code></td><td><code>withLatestFrom</code></td></tr>
<tr><td><code>sampleWith</code></td><td><code>sample</code></td></tr>
<tr><td><code>zip</code></td><td><code>zip</code></td></tr>
<tr><td><code>concat</code></td><td><code>concat</code></td></tr>
<tr><td><code>ap</code></td><td><code>combineLatest</code></td></tr>
</table>

### Side effects 

Produce side effect for every event.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>tap</code></td><td><code>do / tap</code></td></tr>
</table>

### Ending

Operators for special end handling.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>never</code></td><td><code>–</code></td></tr>
</table>

### Concurrency

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>– (<a href="https://github.com/ivan-kleshnin/reactive-polyglot/wiki/race">custom</a>)</code></td><td><code>amb / race</code></td></tr>
</table>

### Notable differences

RxJS does not emit initial `scan` value as event.
MostJS emits initial `scan` value as event.

```js
Rx.Observable.interval(100).map(x => 1)
  .scan(add, 0);
  .subscribe(console.log); // 1--2--3--...

Most.periodic(100, 1)
  .scan(add, 0);
  .observe(console.log); // 0--1--2--3--...
```

### Found docs / API quirks

#### MostJS 

`startWith` vs `sampleWith` vs `continueWith` + `recoverWith` vs `skipRepeatsWith`<br/>
(val vs none vs func vs stream)

`sample` <-> `sampleWith`?

`ap` is listed in "Transform" section.

`tap` is listed in "Transform" section.

#### RxJS

`startWith` is listed in "Combine" section.

`mergeAll` is listed in "Combine" section.

`distinct` is not listed in "Filtering" section.

`takeUntil` is not listed in "Filtering" section.

`just` / `return` should be deprecated in favor of `of`

`fromArray` should be deprecated in favor of `from`

### Tools

[stream-conversions](https://github.com/TylorS/stream-conversions) – convert between different stream implementations
