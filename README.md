# Reactive polyglot

**`R.`** [(Ramda)](http://ramdajs.com/0.19.1/index.html) stands for standard functional toolkit.

## Operators

### Combine

<table>
<tr><th>MostJS</th><th>RxJS</th></tr>
<tr><td><code>merge</code></td><td><code>merge</code></td></tr>
<tr><td><code>combine</code></td><td><code>combineLatest</code></td></tr>
<tr><td><code>sample</code></td><td><code>withLatestFrom</code></td></tr>
<tr><td><code>sampleWith</code></td><td><code>sample</code></td></tr>
<tr><td><code>zip</code></td><td><code>zip</code></td></tr>
<tr><td><code>?</code></td><td><code>amb / race</code></td></tr>
<tr><td><code>concat</code></td><td><code>concat</code></td></tr>
<tr><td><code>flatMap + R.id</code></td><td><code>mergeAll</code></td></tr>
<tr><td><code>of + R.range</code></td><td><code>repeat</code></td></tr>
</table>

