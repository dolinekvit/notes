A Ref is just a mutable object that can store any value. That value will be preserved between re-renders.
A Ref's update **doesn't** trigger re-renders and is **synchronous**.
We can assign a Ref to a DOM element via the `ref` attribute. After that element is rendered, we will see the element in the `ref.current` property.
We can pass Refs as regular props to any component.
If we want to pass it as the actual ref prop, we need to wrap that component in `forwardRef`. Otherwise, it won't work on functional components. The second argument of that component will be the `ref` itself, which we then need to pass down to the desired DOM element.
```
const InputField = forwardRef((props, ref) => <input ref={ref} />)
```
We can hide the implementation details of a component and expose its public API with the `useImperativeHandle` hook. We will need to pass a Ref to that component, which will be mutated with the API properties:
```
const InputField = () => {
    useImperativeHandle(
        outsideRef,
        () => ({
            focus: () => {},
            shake: () => {},
        }),
        []
    )
}
```
Or, we can always just mutate the Ref manually in the useEffect hook:
```
const InputField = ({ apiRef }) => {
    useEffect(() => {
        outsideRef.current = {
            focus: () => {},
            shake: () => {},
        }
    }, [outsideRef])
}
```

