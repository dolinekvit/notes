A high-order component is just a function that accepts a component as an argument and returns a function that returns the said component. 
We can inject props or additional logic into the components that are wrapped in high-order component.
```
// accept a Component as an argument
const withSomeLogic = (Component) => {
  // inject some logic here

  // return a component that renders the component from the argument
  // inject some prop to it
  return (props) => {
    // or inject some logic here
    // can use React hooks here, it's just a component
    return <Component {...props} some="data" />;
  };
};
```
We can pass additional data to the high-order component, either through the function's argument or through props.
