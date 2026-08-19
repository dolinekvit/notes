A race condition can happen when we update state multiple times after a promise is resolved in the same React component.
``` 
useEffect(() => {
    fetch(url)
        .then((r) => r.json())
        .then((r) => {
            setData(r) // this is vulnerable to race condition
        })
}, [url])
```
We can fix it by:
- Forcing a re-mount of a component with the "old" data that we don't need.
- Comparing the returned result with variable  that triggered the promise and not setting state if they don't match.
- Tracing the latest promise via the clean-up function in the `useEffect` and dropping the result of the "old" promises.
- Using `AbortController` to cancel all previous requests.

