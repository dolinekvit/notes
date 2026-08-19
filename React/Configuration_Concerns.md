## Configuration concerns
When a component renders another component, the configuration of which is controlled by props, we can pass the entire component element as a prop instead, leaving the configuration concerns to the consumer.
```
<Button icon={<Error color="red" size="large"} />
```

If a component that has elements as props is rendered conditionally, then even if those elements are created outside of the condition, they will only be rendered when the conditional component is rendered.
If we need to provide default props to the element from props, we can use the `cloneElement` function for that.
This pattern, however, is very fragile. It's too easy to make a mistake there, so use it only for very simple cases.

## Advanced configuration with render props
If a component that has elements as props wants to have control over the props of those elements or pass them, you'll need to convert those elements into render props.
```<Button renderIcon={(props, state) => <Icon {...props} />} />```

Children also can be render props, including "nesting" syntax.
```
const Parent = ({ children }) => {
    return children(somedata)
}

<Parent>
    {(somedata) => <Component />}
</Parent>
```

Render props were very useful when needed to share stateful logic between components without lifting it up.
**Hooks replaced that use case in 99% of cases.**
Render props for sharing stateful logic and data can still be useful even today, for example, when this logic is attached to a DOM element.
