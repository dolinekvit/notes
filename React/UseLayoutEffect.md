When we calculate the dimensions of elements inside the `useEffect` hook and then hide them or adjust their size, we might see the visual "glitch".
This is happening because normally `useEffect` is run asynchronously. Asynchronous code is a separate task from the browser's perspective. So it has a chance to paint the state "before" and "after" the change, resulting in the glitch.
We can prevent this behavior with the `useLayoutEffect` hook. This hook is run synchronously. From the browser's perspective, it will be one large, unbreakable task. So the browser will wait and will not paint anything until the task is complete and the final dimensions are calculated.
In the SSR environment, `useLayoutEffect` will not work since React doesn't run `useLayoutEffect` in SSR mode, and the "glitch" will be visible again.
This can be fixed by opting out of SSR for this specific feature.

