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
