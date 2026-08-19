Uncaught errors in the React lifecycle after version 16 will unmount the entire app. So at least a few ErrorBoundaries in strategic places are non-negotiable.
A simple `try/catch` will catch errors in callbacks or in promises just fine, but it won't be able to catch errors that are coming from any nested components, and you won't be able to wrap `useEffect` or the return of the component in `try/catch`.
The ErrorBoundary component is the opposite. It will catch errors originated in any component down the render tree, but it will skip promises and callbacks (anything async).
We can merge them together and create an uber ErrorBoundary component if we catch the `async` errors with `try/catch` and re-throw them into the normal React lifecycle.
We can either implement a simple `useAsyncError` hook for that or just use the `react-error-boundary` library, which operates on similar principles.

