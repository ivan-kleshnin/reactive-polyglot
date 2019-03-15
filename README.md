# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

### Comparison notes

Operator counterparts aren't and can't be fully equivalent.<br/>
"Kinda the same" – is the current definition.

The following projects, were created with different goals and tradeoffs in mind, so every comparison
and analogy is subjective and can be argued. The presence of some operator is not necessary good, as
well as the abscence is not necessary bad.

Note, that primitives differ for each library. In descriptions, we broadly refer to all the "observable
primitives" as **streams***, though, technically speaking, some of them are rather stream-like entities.

To find something, search for a term you know.

## API

### Create

#### Create an empty stream

* KefirJS: [`never`](http://kefirjs.github.io/kefir/#never)
* MostJS: [`empty`](https://github.com/cujojs/most/blob/master/docs/api.md#mostempty)
* RxJS: [`of`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/of.md)
* XStream: [`empty`](https://github.com/staltz/xstream#of)

#### Create a stream from a single value

* KefirJS: [`constant`](http://kefirjs.github.io/kefir/#constant)
* MostJS: [`of`](https://github.com/cujojs/most/blob/master/docs/api.md#mostjust), [`just`](https://github.com/cujojs/most/blob/master/docs/api.md#mostjust)
* RxJS: [`of`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/of.md), [`just`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/return.md)
* XStream: [`of`](https://github.com/staltz/xstream#of)

#### Create a stream from an array

* KefirJS: [`sequentially`](http://kefirjs.github.io/kefir/#sequentially)
* MostJS: [`from`](https://github.com/cujojs/most/blob/master/docs/api.md#mostfrom)
* RxJS: [`from`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/from.md), [`of`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/of.md)
* XStream: [`from`](https://github.com/staltz/xstream#from), [`fromArray`](https://github.com/staltz/xstream#fromArray)

#### Create a stream from a promise

* KefirJS: [`fromPromise`](http://kefirjs.github.io/kefir/#from-promise)
* MostJS: [`fromPromise`](https://github.com/cujojs/most/blob/master/docs/api.md#mostfrompromise)
* RxJS: [`fromPromise`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/frompromise.md)
* XStream: [`fromPromise`](https://github.com/staltz/xstream#fromPromise)

#### Create a stream from an event

* KefirJS: [`fromEvents`](http://kefirjs.github.io/kefir/#from-event)
* MostJS: [`fromEvent`](https://github.com/cujojs/most/blob/master/docs/api.md#mostfromevent)
* RxJS: [`fromEvent`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/fromevent.md)
* XStream: [`fromEvent`](https://github.com/staltz/xstream/blob/master/EXTRA_DOCS.md#fromEvent)

#### Create a stream from a callback

* KefirJS: [`stream`](http://kefirjs.github.io/kefir/#stream), [`fromCallback`](http://kefirjs.github.io/kefir/#from-callback), [`fromNodeCallback`](http://kefirjs.github.io/kefir/#from-node-callback), [`fromPoll`](http://kefirjs.github.io/kefir/#from-poll)
* MostJS: `new Stream`
* RxJS: `new Observable`, `bindCallback`, `bindNodeCallback`
* XStream: `? (make a promise first)`

#### Prepend a stream with a value

* KefirJS: [`merge`](http://kefirjs.github.io/kefir/#merge) `+` [`constant`](http://kefirjs.github.io/kefir/#constant)
* MostJS: `startWith`
* RxJS: [`startWith`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/startwith.md)
* XStream: `startWith`

### Transform (data events)

#### Map value one-to-one

* KefirJS: [`map`](http://kefirjs.github.io/kefir/#map)
* MostJS: `map`, `constant`
* RxJS: [`map`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/select.md), `mapTo`
* XStream: `map`

#### Filter value by a predicate

* KefirJS: [`filter`](http://kefirjs.github.io/kefir/#filter)
* MostJS: `filter`
* RxJS: [`filter`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/where.md)
* XStream: `filter`

#### Skip N initial values

* KefirJS: [`skip`](http://kefirjs.github.io/kefir/#skip)
* MostJS: `skip`
* RxJS: [`skip`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/skip.md)
* XStream: `drop`

#### Take N initial values

* KefirJS: [`take`](http://kefirjs.github.io/kefir/#take)
* MostJS: `take`
* RxJS: [`take`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/take.md)
* XStream: `take`

#### Make a value from an accumulator and a next value

* KefirJS: [`scan`](http://kefirjs.github.io/kefir/#scan)
* MostJS: `scan`
* RxJS: [`scan`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/scan.md)
* XStream: `fold`

### Combine

#### Merge multiple streams together

* KefirJS: [`merge`](http://kefirjs.github.io/kefir/#merge)
* MostJS: `merge`
* RxJS: [`merge`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/merge.md)
* XStream: `merge`

Pay attention that Kefir's `merge` accepts arrays while others are variadic.

#### Combine multiple streams together

* KefirJS: [`combine`](http://kefirjs.github.io/kefir/#combine)
* MostJS: `combine`
* RxJS: [`combineLatest`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/combinelatest.md)
* XStream: `combine`

#### Sample a stream by another stream

* KefirJS: [`combine`](http://kefirjs.github.io/kefir/#combine), [`sampledBy`](http://kefirjs.github.io/kefir/#obs-sampled-by)
* MostJS: `sample`, `sampleWith`
* RxJS: [`sample`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/sample.md), [`withLatestFrom`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/withlatestfrom.md)
* XStream: `sampleCombine`

#### Chain streams sequentially

* KefirJS: [`flatMapConcat`](http://kefirjs.github.io/kefir/#flat-map-concat)
* MostJS: [`concatMap`](https://github.com/cujojs/most/blob/master/docs/api.md#concatmap)
* RxJS: [`concatMap`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/concatmap.md)
* XStream: `map + flattenSequentially`

---

### Create

Create stream from non-stream values.

<table>
<tr>
  <th>KefirJS</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>interval</code></td>
  <td><code>periodic</code></td>
  <td><code>interval + map</code></td>
  <td><code>periodic</code></td>
</tr>
<tr>
  <td><code>repeat</code></td>
  <td><code>of + R.range</code></td>
  <td><code>repeat</code></td>
  <td><code>of + R.range</code></td>
</tr>
<tr>
  <td><code>?</code></td>
  <td><code>iterate</code></td>
  <td><code>generate</code></td>
  <td>?</td>
</tr>
<tr>
  <td><code>?</code></td>
  <td><code>generate</code></td>
  <td><code>generate</code></td>
  <td>?</td>
</tr>
</table>

### Mapper

Modify events one to one.

<table>
<tr>
  <th>KefirJS</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>delay</code></td>
  <td><code>delay</code></td>
  <td><code>delay</code></td>
  <td><code>combine(delay(500))</code></td>
</tr>
<tr>
  <td><code>– (map)</code></td>
  <td><code>timestamp</code></td>
  <td><code>timestamp</code></td>
  <td><code>– (map)</code></td>
</tr>
</table>

### Transforms

Modify events * to *.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>chain / flatMap</code></td>
  <td><code>flatMap</code></td>
  <td><code>map + flattenConcurrently</code></td>
</tr>
<tr>
  <td><code>map + switch</code></td>
  <td><code>switchMap / flatMapLatest</code></td>
  <td><code>map + flatten</code></td>
</tr>
<tr>
  <td><code>join</code></td>
  <td><code>mergeAll</code></td>
  <td><code>flatten</code></td>
</tr>
<tr>
  <td><code>loop</code></td>
  <td><code>scan + map</code></td>
  <td><code>fold + map</code></td>
</tr>
<tr>
  <td><code>– (<a href="bufferWithCount.md">custom</a>)</code></td>
  <td><code>bufferWithCount</code></td>
  <td>?</td>
</tr>
</table>

### Filters

Skip events by predicate or signal.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>skipRepeats</code></td>
  <td><code>distinctUntilChanged</code></td>
  <td><code>dropRepeats</code></td>
</tr>
<tr>
  <td><code>skipRepeatsWith</code></td>
  <td><code>– (scan)</code></td>
  <td><code>dropRepeats</code></td>
</tr>
<tr>
  <td><code>slice</code></td>
  <td><code>skip + take</code></td>
  <td><code>drop + take</code></td>
</tr>
<tr>
  <td><code>skipWhile</code></td>
  <td><code>skipWhile</code></td>
  <td><code>fold + filter + map</code></td>
</tr>
<tr>
  <td><code>takeWhile</code></td>
  <td><code>takeWhile</code></td>
  <td><code>filter + endWhen</code></td>
</tr>
<tr>
  <td><code>since / skipUntil</code></td>
  <td><code>skipUntil</code></td>
  <td><code>fold + filter + map</code></td>
</tr>
<tr>
  <td><code>until / takeUntil</code></td>
  <td><code>takeUntil</code></td>
  <td><code>filter + endWhen</code></td>
</tr>
<tr>
  <td><code>during</code></td>
  <td><code>window + take(1)</code></td>
  <td>?</td>
</tr>
</table>

### Combinators

Combine multiple streams into single.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>zip</code></td>
  <td><code>zip</code></td>
  <td>?</td>
</tr>
<tr>
  <td><code>concat</code></td>
  <td><code>concat</code></td>
  <td><code>concat</code></td>
</tr>
<tr>
  <td><code>ap</code></td>
  <td><code>combineLatest</code></td>
  <td>?</td>
</tr>
</table>

### Side effects

Produce side effect for every event.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>tap</code></td>
  <td><code>do / tap</code></td>
  <td><code>debug</code></td>
</tr>
</table>

### Ending

Operators which target **end** event somehow.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>empty</code></td>
  <td><code>empty</code></td>
  <td><code>empty</code></td>
</tr>
<tr>
  <td><code>never</code></td>
  <td><code>never</code></td>
  <td><code>never</code></td>
</tr>
<tr>
  <td><code>continueWith</code></td>
  <td><code>?</code></td>
  <td><code>concat</code></td>
</tr>
</table>

### Concurrency

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
</tr>
<tr>
  <td><code>– (<a href="https://github.com/ivan-kleshnin/reactive-polyglot/wiki/race">custom</a>)</code></td>
  <td><code>amb / race</code></td>
</tr>
</table>

### History

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
</tr>
<tr>
  <td colspan="2"><code>– (<a href="history.md">custom</a>)</code></td>
</tr>
</table>

### Design diffs

#### RxJS

1. Three primitives: `Observer`, `Observable`, `Subject`.
2. Observables end on error.
3. Provides API to handle errors.
3. Does not provide API to handle ending.

#### KefirJS

1. Two primitives: `Stream` and `Property` (like XStream).
2. Observables does not end on error (by default).
3. Provides API to handle errors.
4. Provides API to handle ending.

#### MostJS

1. One primitive: `Stream` (+ community-driven).
2. Separate packages for [subject-like](https://github.com/TylorS/most-subject) and [property-like](https://github.com/mostjs/hold) primitives.
3. Provides API to handle errors.
4. Provides API to handle ending.

#### XStream

1. Two primitives: `Stream` and `MemoryStream` (like KefirJS).
2. Always multicast. A Stream is like an RxJS Subject.
3. Streams end on error.

#### Common

RxJS does not emit initial `scan` value as event (use `startWith` for that).

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

### Links

[bacon-vs-kefir](https://github.com/rpominov/kefir/blob/master/bacon-vs-kefir-api.md) – BaconJS vs KefirJS API comparison

[dataflows](https://github.com/ivan-kleshnin/dataflows) – web arch. dataflow comparison

[stream-conversions](https://github.com/TylorS/stream-conversions) – tool for cross-library stream conversions

### Additional Read

https://github.com/cujojs/most/issues/171

https://twitter.com/rpominov/status/689566111734599683

https://github.com/zenparsing/es-observable/issues/66

# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

### Comparison notes

Operator counterparts aren't and can't be fully equivalent.<br/>
"Kinda the same" – is the current definition.

The following projects, were created with different goals and tradeoffs in mind, so every comparison
and analogy is subjective and can be argued. The presence of some operator is not necessary good, as
well as the abscence is not necessary bad.

Note, that primitives differ for each library. In descriptions, we broadly refer to all the "observable
primitives" as **streams***, though, technically speaking, some of them are rather stream-like entities.

To find something, search for a term you know.

## API

### Create

#### Create an empty stream

* KefirJS: [`never`](http://kefirjs.github.io/kefir/#never)
* MostJS: [`empty`](https://github.com/cujojs/most/blob/master/docs/api.md#mostempty)
* RxJS: [`of`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/of.md)
* XStream: [`empty`](https://github.com/staltz/xstream#of)

#### Create a stream from a single value

* KefirJS: [`constant`](http://kefirjs.github.io/kefir/#constant)
* MostJS: [`of`](https://github.com/cujojs/most/blob/master/docs/api.md#mostjust), [`just`](https://github.com/cujojs/most/blob/master/docs/api.md#mostjust)
* RxJS: [`of`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/of.md), [`just`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/return.md)
* XStream: [`of`](https://github.com/staltz/xstream#of)

#### Create a stream from an array

* KefirJS: [`sequentially`](http://kefirjs.github.io/kefir/#sequentially)
* MostJS: [`from`](https://github.com/cujojs/most/blob/master/docs/api.md#mostfrom)
* RxJS: [`from`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/from.md), [`of`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/of.md)
* XStream: [`from`](https://github.com/staltz/xstream#from), [`fromArray`](https://github.com/staltz/xstream#fromArray)

#### Create a stream from a promise

* KefirJS: [`fromPromise`](http://kefirjs.github.io/kefir/#from-promise)
* MostJS: [`fromPromise`](https://github.com/cujojs/most/blob/master/docs/api.md#mostfrompromise)
* RxJS: [`fromPromise`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/frompromise.md)
* XStream: [`fromPromise`](https://github.com/staltz/xstream#fromPromise)

#### Create a stream from an event

* KefirJS: [`fromEvents`](http://kefirjs.github.io/kefir/#from-event)
* MostJS: [`fromEvent`](https://github.com/cujojs/most/blob/master/docs/api.md#mostfromevent)
* RxJS: [`fromEvent`](https://github.com/Reactive-Extensions/RxJS/blob/master/doc/api/core/operators/fromevent.md)
* XStream: [`fromEvent`](https://github.com/staltz/xstream/blob/master/EXTRA_DOCS.md#fromEvent)

#### Create a stream from a callback

* KefirJS: [`stream`](http://kefirjs.github.io/kefir/#stream), [`fromCallback`](http://kefirjs.github.io/kefir/#from-callback), [`fromNodeCallback`](http://kefirjs.github.io/kefir/#from-node-callback), [`fromPoll`](http://kefirjs.github.io/kefir/#from-poll)
* MostJS: `new Stream`
* RxJS: `new Observable`, `bindCallback`, `bindNodeCallback`
* XStream: `? (make a promise first)`

#### Prepend a stream with a value

* KefirJS: [`merge`](http://kefirjs.github.io/kefir/#merge) `+` [`constant`](http://kefirjs.github.io/kefir/#constant)
* MostJS: `startWith`
* RxJS: `startWith`
* XStream: `startWith`

### Transform (data events)

#### Map value one-to-one

* KefirJS: [`map`](http://kefirjs.github.io/kefir/#map)
* MostJS: `map`, `constant`
* RxJS: `map`, `mapTo`
* XStream: `map`

#### Filter value by a predicate

* KefirJS: [`filter`](http://kefirjs.github.io/kefir/#filter)
* MostJS: `filter`
* RxJS: `filter`
* XStream: `filter`

#### Skip N initial values

* KefirJS: [`skip`](http://kefirjs.github.io/kefir/#skip)
* MostJS: `skip`
* RxJS: `skip`
* XStream: `drop`

#### Take N initial values

* KefirJS: [`take`](http://kefirjs.github.io/kefir/#take)
* MostJS: `take`
* RxJS: `take`
* XStream: `take`

#### Make a value from an accumulator and a next value

* KefirJS: [`scan`](http://kefirjs.github.io/kefir/#scan)
* MostJS: `scan`
* RxJS: `scan`
* XStream: `fold`

### Combine

#### Merge multiple streams together

* KefirJS: [`merge`](http://kefirjs.github.io/kefir/#merge)
* MostJS: `merge`
* RxJS: `merge`
* XStream: `merge`

Pay attention that Kefir's `merge` accepts arrays while others are variadic.

#### Combine multiple streams together

* KefirJS: [`combine`](http://kefirjs.github.io/kefir/#combine)
* MostJS: `combine`
* RxJS: `combineLatest`
* XStream: `combine`

#### Sample a stream by another stream

* KefirJS: [`combine`](http://kefirjs.github.io/kefir/#combine), [`sampledBy`](http://kefirjs.github.io/kefir/#obs-sampled-by)
* MostJS: `sample`, `sampleWith`
* RxJS: `sample`, `withLatestFrom`
* XStream: `sampleCombine`

#### Chain streams sequentially

* KefirJS: [`flatMapConcat`](http://kefirjs.github.io/kefir/#flat-map-concat)
* MostJS: `concatMap`
* RxJS: `concatMap`
* XStream: `map + flattenSequentially`

---

### Create

Create stream from non-stream values.

<table>
<tr>
  <th>KefirJS</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>interval</code></td>
  <td><code>periodic</code></td>
  <td><code>interval + map</code></td>
  <td><code>periodic</code></td>
</tr>
<tr>
  <td><code>repeat</code></td>
  <td><code>of + R.range</code></td>
  <td><code>repeat</code></td>
  <td><code>of + R.range</code></td>
</tr>
<tr>
  <td><code>?</code></td>
  <td><code>iterate</code></td>
  <td><code>generate</code></td>
  <td>?</td>
</tr>
<tr>
  <td><code>?</code></td>
  <td><code>generate</code></td>
  <td><code>generate</code></td>
  <td>?</td>
</tr>
</table>

### Mapper

Modify events one to one.

<table>
<tr>
  <th>KefirJS</th>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>delay</code></td>
  <td><code>delay</code></td>
  <td><code>delay</code></td>
  <td><code>combine(delay(500))</code></td>
</tr>
<tr>
  <td><code>– (map)</code></td>
  <td><code>timestamp</code></td>
  <td><code>timestamp</code></td>
  <td><code>– (map)</code></td>
</tr>
</table>

### Transforms

Modify events * to *.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>chain / flatMap</code></td>
  <td><code>flatMap</code></td>
  <td><code>map + flattenConcurrently</code></td>
</tr>
<tr>
  <td><code>map + switch</code></td>
  <td><code>switchMap / flatMapLatest</code></td>
  <td><code>map + flatten</code></td>
</tr>
<tr>
  <td><code>join</code></td>
  <td><code>mergeAll</code></td>
  <td><code>flatten</code></td>
</tr>
<tr>
  <td><code>loop</code></td>
  <td><code>scan + map</code></td>
  <td><code>fold + map</code></td>
</tr>
<tr>
  <td><code>– (<a href="bufferWithCount.md">custom</a>)</code></td>
  <td><code>bufferWithCount</code></td>
  <td>?</td>
</tr>
</table>

### Filters

Skip events by predicate or signal.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>skipRepeats</code></td>
  <td><code>distinctUntilChanged</code></td>
  <td><code>dropRepeats</code></td>
</tr>
<tr>
  <td><code>skipRepeatsWith</code></td>
  <td><code>– (scan)</code></td>
  <td><code>dropRepeats</code></td>
</tr>
<tr>
  <td><code>slice</code></td>
  <td><code>skip + take</code></td>
  <td><code>drop + take</code></td>
</tr>
<tr>
  <td><code>skipWhile</code></td>
  <td><code>skipWhile</code></td>
  <td><code>fold + filter + map</code></td>
</tr>
<tr>
  <td><code>takeWhile</code></td>
  <td><code>takeWhile</code></td>
  <td><code>filter + endWhen</code></td>
</tr>
<tr>
  <td><code>since / skipUntil</code></td>
  <td><code>skipUntil</code></td>
  <td><code>fold + filter + map</code></td>
</tr>
<tr>
  <td><code>until / takeUntil</code></td>
  <td><code>takeUntil</code></td>
  <td><code>filter + endWhen</code></td>
</tr>
<tr>
  <td><code>during</code></td>
  <td><code>window + take(1)</code></td>
  <td>?</td>
</tr>
</table>

### Combinators

Combine multiple streams into single.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>zip</code></td>
  <td><code>zip</code></td>
  <td>?</td>
</tr>
<tr>
  <td><code>concat</code></td>
  <td><code>concat</code></td>
  <td><code>concat</code></td>
</tr>
<tr>
  <td><code>ap</code></td>
  <td><code>combineLatest</code></td>
  <td>?</td>
</tr>
</table>

### Side effects

Produce side effect for every event.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>tap</code></td>
  <td><code>do / tap</code></td>
  <td><code>debug</code></td>
</tr>
</table>

### Ending

Operators which target **end** event somehow.

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
  <th>XStream</th>
</tr>
<tr>
  <td><code>empty</code></td>
  <td><code>empty</code></td>
  <td><code>empty</code></td>
</tr>
<tr>
  <td><code>never</code></td>
  <td><code>never</code></td>
  <td><code>never</code></td>
</tr>
<tr>
  <td><code>continueWith</code></td>
  <td><code>?</code></td>
  <td><code>concat</code></td>
</tr>
</table>

### Concurrency

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
</tr>
<tr>
  <td><code>– (<a href="https://github.com/ivan-kleshnin/reactive-polyglot/wiki/race">custom</a>)</code></td>
  <td><code>amb / race</code></td>
</tr>
</table>

### History

<table>
<tr>
  <th>MostJS</th>
  <th>RxJS</th>
</tr>
<tr>
  <td colspan="2"><code>– (<a href="history.md">custom</a>)</code></td>
</tr>
</table>

### Design diffs

#### RxJS

1. Three primitives: `Observer`, `Observable`, `Subject`.
2. Observables end on error.
3. Provides API to handle errors.
3. Does not provide API to handle ending.

#### KefirJS

1. Two primitives: `Stream` and `Property` (like XStream).
2. Observables does not end on error (by default).
3. Provides API to handle errors.
4. Provides API to handle ending.

#### MostJS

1. One primitive: `Stream` (+ community-driven).
2. Separate packages for [subject-like](https://github.com/TylorS/most-subject) and [property-like](https://github.com/mostjs/hold) primitives.
3. Provides API to handle errors.
4. Provides API to handle ending.

#### XStream

1. Two primitives: `Stream` and `MemoryStream` (like KefirJS).
2. Always multicast. A Stream is like an RxJS Subject.
3. Streams end on error.

#### Common

RxJS does not emit initial `scan` value as event (use `startWith` for that).

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

### Links

[bacon-vs-kefir](https://github.com/rpominov/kefir/blob/master/bacon-vs-kefir-api.md) – BaconJS vs KefirJS API comparison

[dataflows](https://github.com/ivan-kleshnin/dataflows) – web arch. dataflow comparison

[stream-conversions](https://github.com/TylorS/stream-conversions) – tool for cross-library stream conversions

### Additional Read

https://github.com/cujojs/most/issues/171

https://twitter.com/rpominov/status/689566111734599683

https://github.com/zenparsing/es-observable/issues/66


