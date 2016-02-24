# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

## Operators

Current ordering is subjective: from most common operators to less common.<br/>
Operator counterparts are not expected to be fully equivalent.<br/>
"Kinda the same" is the current definition.

Presence of operator is not "good" as well as abscence is not "bad".<br/> 
Every decision has it's own benefits and drawbacks.
Remember, that we're trying to make analogies over systems which were be designed
with different goals / philosophies in mind.

### Create

Create stream from non-stream values.

<table>
<tr><th>Elm</th><th>KefirJS</th><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>constant</code></td><td><code>constant</code></td><td><code>of / just</code></td><td><code>just</code></td></tr>
<tr><td>?</td><td><code>– (sequentially)</code></td><td><code>– (from)</code></td><td><code>of</code></td></tr>
<tr><td>?</td><td><code>– (sequentially)</code></td><td><code>from</code></td><td><code>from</code></td></tr>
<tr><td>?</td><td><code>fromEvents</code></td><td><code>fromEvent</code></td><td><code>fromEvent</code></td></tr>
<tr><td>?</td><td><code>fromPromise</code></td><td><code>fromPromise</code></td><td><code>fromPromise</code></td></tr>
<tr><td><code>Time.every</code></td><td><code>interval</code></td><td><code>periodic</code></td><td><code>interval + map</code></td></tr>
<tr><td><code>–</code></td><td><code>repeat</code></td><td><code>of + R.range</code></td><td><code>repeat</code></td></tr>
<tr><td><code>–</code></td><td><code>repeat</code></td><td><code>iterate</code></td><td><code>generate</code></td></tr>
<tr><td><code>–</code></td><td><code>repeat</code></td><td><code>generate</code></td><td><code>generate</code></td></tr>
</table>

### Mapper

Modify events one to one.

<table>
<tr><th>Elm</th><th>KefirJS</th><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>map</code></td><td><code>map</code></td><td><code>map</code></td></tr>
<tr><td>?</td><td><code>– (map)</code></td><td><code>constant</code></td><td><code>mapTo</code></td></tr>
<tr><td>?</td><td><code>delay</code></td><td><code>delay</code></td><td><code>delay</code></td></tr>
<tr><td>?</td><td><code>– (map)</code></td><td><code>timestamp</code></td><td><code>timestamp</code></td></tr>
</table>

### Transforms

Modify events * to *.

<table>
<tr><th>Elm</th><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>foldp</code></td><td><code>scan</code></td><td><code>scan</code></td></tr>
<tr><td><code>– (filterMap)</code></td><td><code>chain / flatMap</code></td><td><code>flatMap</code></td></tr>
<tr><td>?</td><td><code>concatMap</code></td><td><code>concatMap</code></td></td></tr>
<tr><td>?</td><td><code>join</code></td><td><code>mergeAll</code></td></td></tr>
<tr><td>?</td><td><code>loop</code></td><td><code>scan + map</code></td></td></tr>
<tr><td>?</td><td><code>– (<a href="bufferWithCount.md">custom</a>)</code></td><td><code>bufferWithCount</code></td></td></tr>
</table>

### Filters

Skip events by predicate or signal.

<table>
<tr><th>Elm</th><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>filter</code></td><td><code>filter</code></td><td><code>filter</code></td></tr>
<tr><td><code>dropRepeats</code></td><td><code>skipRepeats</code></td><td><code>distinctUntilChanged</code></td></tr>
<tr><td>?</td><td><code>skipRepeatsWith</code></td><td><code>– (scan)</code></td></tr>
<tr><td>?</td><td><code>skip</code></td><td><code>skip</code></td></tr>
<tr><td>?</td><td><code>take</code></td><td><code>take</code></td></tr>
<tr><td>?</td><td><code>slice</code></td><td><code>skip + take</code></td>/tr>
<tr><td>?</td><td><code>skipWhile</code></td><td><code>skipWhile</code></td></tr>
<tr><td>?</td><td><code>takeWhile</code></td><td><code>takeWhile</code></td></tr>
<tr><td>?</td><td><code>since / skipUntil</code></td><td><code>skipUntil</code></td></tr>
<tr><td>?</td><td><code>until / takeUntil</code></td><td><code>takeUntil</code></td></tr>
<tr><td>?</td><td><code>during</code></td><td><code>window + take(1)</code></td></tr>
</table>

### Combinators

Combine multiple streams into single.

<table>
<tr><th>Elm</th><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>merge / mergeMany</code></td><td><code>merge</code></td><td><code>merge</code></td></tr>
<tr><td><code>map2 / map3...</code> <code><~ / ~</code></td><td><code>combine</code></td><td><code>combineLatest</code></td></tr>
<tr><td><code>sampleOn</code></td><td><code>sample</code></td><td><code>withLatestFrom</code></td></tr>
<tr><td><code>sampleOn + Time.every</code></td><td><code>sampleWith</code></td><td><code>sample</code></td></tr>
<tr><td>?</td><td><code>zip</code></td><td><code>zip</code></td></tr>
<tr><td>?</td><td><code>concat</code></td><td><code>concat</code></td></tr>
<tr><td>?</td><td><code>ap</code></td><td><code>combineLatest</code></td></tr>
</table>

### Side effects 

Produce side effect for every event.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>tap</code></td><td><code>do / tap</code></td></tr>
</table>

### Ending

Operators which target end event somehow.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>never</code></td><td><code>never</code></td></tr>
<tr><td><code>continueWith</code></td><td><code>?</code></td></tr>
</table>

### Concurrency

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>– (<a href="https://github.com/ivan-kleshnin/reactive-polyglot/wiki/race">custom</a>)</code></td><td><code>amb / race</code></td></tr>
</table>

### History

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td colspan="2"><code>– (<a href="history.md">custom</a>)</code></td></tr>
</table>

### Notable differences

RxJS does not emit initial `scan` value as event (see `startWith`).
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

`tap` is listed in "Transform" section.

#### RxJS

`startWith` is listed in "Combine" section.

`mergeAll` is listed in "Combine" section.

`distinct` is not listed in "Filtering" section.

`takeUntil` is not listed in "Filtering" section.

`just` / `return` should be deprecated in favor of `of`.

`fromArray` should be deprecated in favor of `from`.

### Tools

[stream-conversions](https://github.com/TylorS/stream-conversions) – convert between different stream implementations
