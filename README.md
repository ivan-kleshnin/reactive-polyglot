# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

## Operators

### Create

Create stream from non-stream values.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>of + R.range</code></td><td><code>repeat</code></td></tr>
<tr><td>...</td><td>...</td></tr>
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
</table>

### Filter

Skip events by predicate or signal.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>filter</code></td><td><code>filter</code></td></tr>
<tr><td><code>skipRepeats</code></td><td><code>distinctUntilChanged</code></td></tr>
<tr><td><code>skipRepeatsWith</code></td><td><code>– (scan)</code></td></tr>
<tr><td><code>slice</code></td><td><code>skip + take</code></td></tr>
<tr><td><code>take</code></td><td><code>take</code></td></tr>
<tr><td><code>skip</code></td><td><code>skip</code></td></tr>
<tr><td><code>takeWhile</code></td><td><code>takeWhile</code></td></tr>
<tr><td><code>until / takeUntil</code></td><td><code>takeUntil</code></td></tr>
<tr><td><code>skipWhile</code></td><td><code>skipWhile</code></td></tr>
<tr><td><code>since / skipUntil</code></td><td><code>skipUntil</code></td></tr>
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
