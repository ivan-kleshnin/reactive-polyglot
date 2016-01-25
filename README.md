# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

## Operators

### Map

Map values of a stream to a different stream (1 to 1).

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>map</code></td><td><code>map</code></td></tr>
<tr><td><code>constant</code></td><td><code>mapTo</code></td></tr>
<tr><td><code>timestamp</code></td><td><code>timestamp</code></td></tr>
</table>

### Transform

Transform stream values in general way (* to *).

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>chain / flatMap</code></td><td><code>flatMap</code></td></tr>
<tr><td><code>concatMap</code></td><td><code>concatMap</code></td></tr>
<tr><td><code>join</code></td><td><code>mergeAll</code></td></tr>
</table>

### Filter by predicate

Skip stream values by predicate.

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
</table>

### Filter by signal

Skip stream values by time / signal.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>during</code></td><td><code>window + take(1)</code></td></tr>
</table>

### Combine 

Combine multiple streams into single stream.

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>merge</code></td><td><code>merge</code></td></tr>
<tr><td><code>combine</code></td><td><code>combineLatest</code></td></tr>
<tr><td><code>sample</code></td><td><code>withLatestFrom</code></td></tr>
<tr><td><code>sampleWith</code></td><td><code>sample</code></td></tr>
<tr><td><code>zip</code></td><td><code>zip</code></td></tr>
<tr><td><code>concat</code></td><td><code>concat</code></td></tr>
<tr><td><code>ap</code></td><td><code>combineLatest</code></td></tr>
<tr><td><code>of + R.range</code></td><td><code>repeat</code></td></tr>
</table>

### Unsorted

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>?</code></td><td><code>amb / race</code></td></tr>
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
