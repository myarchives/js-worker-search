Changelog
-----

#### 1.1.0
Added support for custom index strategies.
By default, a prefix matching strategy is still used but it can be overridden like so:

```js
import SearchApi, { INDEX_MODES } from 'js-worker-search'

// all-substrings match by default; same as current
// eg "c", "ca", "a", "at", "cat" match "cat"
const searchApi = new SearchApi()

// prefix matching (eg "c", "ca", "cat" match "cat")
const searchApi = new SearchApi({
  indexMode: INDEX_MODES.PREFIXES
})

// exact words matching (eg only "cat" matches "cat")
const searchApi = new SearchApi({
  indexMode: INDEX_MODES.EXACT_WORDS
})
```

#### 1.0.2
Wrapped `String.prototype.charAt` usage in a `try/catch` to avoid erroring when handling surrogate halves.
In the context of a web-worker, non-BMP characters seem to cause Chrome 49.0 to crash.

#### 1.0.1
Bound indexSearch and search methods to prevent them from losing context when passed around.

# 1.0.0
Initial release; forked from [redux-search](https://github.com/treasure-data/redux-search).