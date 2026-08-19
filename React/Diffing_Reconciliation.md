React will compare elements between re-renders with elements in the same place in the returned array on any level of hierarchy. The first one with the first one, the second one with second one, etc.
If the type of the element and its position in the array is the same, React will re-render that element. If the type changes at that position, then React will unmount the previous component and mount the new one.
An array of children will always have the same number of children (if it's not dynamic). Conditional elements (`isSomething ? <A /> : <B />`) will take just one place, even if one if them is null.
If the array is dynamic, then React can't reliably identify those elements between re-renders. So we can use the `key` attribute to help it. This is important when the array can change the number of its items or their position between re-renders and especially important if those elements are wrapped in `React.memo`.
We can use the `key` outside of dynamic arrays as well to force React to recognize elements at the same position in the array with the same type as different. Or to force it to recognize elements at different positions with the same type as t he same.
We can also force unmounting of a component with a `key` if that key changes between re-renders based on some information (like routing). This is sometimes called "state reset".

