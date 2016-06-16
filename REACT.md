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

## Workshop by nodeschool
https://github.com/kohei-takata/learnyoureact
