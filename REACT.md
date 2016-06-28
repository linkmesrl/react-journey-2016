# React
- [component lifecycle](http://dbertella.github.io/react-lifecycle-svg/)
  ![react lifecycle](./img/react-lifecycle.png)
- props
- state

Nice to have
- immutable.js
- Server side rendering

## JSX


## ES2015 syntax
```
import React from 'react';

class MyComponent extends React.Component {
  constructor() {
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick = () => {
    console.log('hello world');
  };
  render() {
    return (
      <button onClick={this.handleClick}>Say Hello</button>
    );
  }
}
Contacts.propTypes = {

};
Contacts.defaultProps = {

};

export default MyComponent;
```
## React Router

- Router
  `<Router history={browserHistory}>`
- Route
  `<Route path="/(:filter)" component={App}` />
  () means optional parameter
- Link
  `<Link to={filter} activeStyle={{ textDecoration: 'none' }}`>
  activeStyle prop -> prop to style the active route in Link component

React router > 3.x.x `withRouter`

`withRouter(connect(Component))`: HoC that inject react router props into component (using with redux)

## Hoc
```
import React, { Component } from "React";

export const Enhance = ComposedComponent => class extends Component {
  constructor() {
    this.state = { data: null };
  }
  componentDidMount() {
    this.setState({ data: 'Hello' });
  }
  render() {
    return <ComposedComponent {...this.props} data={this.state.data} />;
  }
};
```

```
import React, { Component } from 'React';

export const Enhance = ComposedComponent => {
  class NewComponent extends Component {
    constructor() {
      this.state = { data: null };
    }
    componentDidMount() {
      this.setState({ data: 'Hello' });
    }
    render() {
      return <ComposedComponent {...this.props} data={this.state.data} />;
    }
  }
  NewComponent.propTypes = {
    // whatever
  };
  return NewComponent;
};
```
http://rea.tech/reactjs-real-world-examples-of-higher-order-components/

## Enzyme (link)[http://airbnb.io/enzyme/]
Before react testing the UI it's always been hard.
Testing single components and not the entire UI is the key to simplify the process.

> Pure functions (and thus React components) are much easier to test because they simply return a description for what UI of the component should look like, given some application state, rather than actually mutating the UI and having side-effects. This “description” is known as a “Virtual DOM” and is a tree-like data structure.
[link](https://medium.com/airbnb-engineering/enzyme-javascript-testing-utilities-for-react-a417e5e5090f#.jolxe9mz8)

Enzyme exports three different “modes” to render and test components, **shallow**, **mount**, and **render**. Shallow is the recommended mode to start with since it does a better job of isolating your tests to just a single component. If shallow doesn’t work for your use case (for example, if you are relying on the presence of a real DOM), mount or render likely will.

You can use it with every test library and assertion library. You can use it for unit and integration test.

Shallow rendering:  
`const wrapper = shallow(<Foo />);`

```
it('renders the title', () => {
  const item = {
    title: 'New Item',
    completed: false,
  };
  const wrapper = shallow(<ToDoItem item={item} />);
  expect(wrapper.text()).to.contain(item.title);
});
```

**Enzyme Selectors**  
Enzyme Selectors can find nodes by 4 categories:
- CSS selectors `.class`, `#id`, `tag`, `[prop="text"]`: `wrapper.find('.class')`
- component constructor `wrapper.find(Component)`
- display name `wrapper.find('ComponentDisplayName')`
- object properties `wrapper.find({ prop: text })`

**Event simulations**

Enzyme gives you a concise and elegant way of simulating user events, one of the trickier aspects of UI testing. Just pass the name of the event you want to simulate, along with any required data:

```
wrapper.simulate('click', {
  stopPropagation() { console.log('Stopped propagation'); }
})
```

Debug:  
`console.log(wrapper.debug())` > nicely formatted JSX

## Workshop by nodeschool
https://github.com/kohei-takata/learnyoureact
