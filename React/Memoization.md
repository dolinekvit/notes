Usage of `React.memo` should be the last resort when all other things have failed.
React compares object/arrays/functions by their reference (in memory), not their value. That comparison happens in hooks' dependencies and in props of components wrapped in `React.memo`.
The inline function passed as an argument to either `useMemo` or `useCallback` will be re-created on every re-render. `useCallback` memoizes that function itself, `useMemo` memoizes the result of its execution.
Memoizing props on a component makes sense only when:
-- The component is wrapped in `React.memo`.
-- The component uses those props as dependencies in any of the hooks.
-- The component passes those props down to other components, and they have either of the situations from above.
If a component is wrapped in `React.memo` and its re-render is triggered by its parent, the React will not re-render this component if props haven't changed. In any other case, re-render will proceed as usual.
Memoizing all props on a component wrapped in `React.memo` is harder than it seems. Avoid passing non-primitive values that are coming from other props or hooks to it.
When memoizing props, remember that "children" is also a non-primitive prop that **needs to be memoized**.
