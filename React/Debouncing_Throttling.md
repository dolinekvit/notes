We use debounce and throttle when we want to skip some function's executions that were fired too often.
In order for those functions to work properly, they should be called only once in a component's life, usually when it's mounted.
If we call them in the component's render function directly, the timer inside will be re-created with every re-render, and the functions will not work as expected.
To fix this, we can memoize those with useMemo or through the usage of Refs.
If we simply memoize them or use Refs "naively", we won't have access to the component's latest data, like state or props. This is happening because a closure is created when we initialize Ref, which freezes values at the time it's created.
To escape the closure trap, we can leverage the mutable nature of the Ref object and gain access to the latest data by constantly updating the "closed" function in `ref.current` within `useEffect`.
```
useEffect(() => {
    ref.current = callback
}) // triggered on every re-render
```


```
const useDebounce = (callback) => {
    const ref = useRef(callback) // memoize callback
    const memo = useMemo(() => debounce(() => ref.current?.(), 500))

    useEffect(() => {
        ref.current = callback // reassign
    })

    return memo;
}
```
