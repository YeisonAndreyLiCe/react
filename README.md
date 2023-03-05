# React 
Single page application.
We can integrate it in an easy way

## components
Divide and allows to reuse.

```bash
npx create-react-app {route}
cd {route}
npm start 
```
## Function base component
```javascript
import React from 'react';
```

## JSX
elements must be wrapping 
Only one principal element 

## Class based component
```javascript
//App.js
import React from 'react';

class App extends React.Component {
    render() {
        return (
        <div className="App">
            <h1>Hello, world!</h1>
        </div>
        );
    }
}
```
```bash
cd src
mkdir components
mkdir PascalCaseName
cd PascalCaseName
touch PascalCaseName.js
```
```javascript
//PascalCaseName.js
import React from 'react';

class PascalCaseName extends React.Component {
    render() {
        return (
        <div>
            <h1>Hello, world!</h1>
        </div>
        );
    }
}

export default PascalCaseName;
```
```javascript
//App.js
import React from 'react';
import PascalCaseName from './components/PascalCaseName/PascalCaseName';

class App extends React.Component {
    render() {
        return (
        <div className="App">
            <PascalCaseName />
        </div>
        );
    }
}
```

## Props
```javascript
//PascalCaseName.js
import React from 'react';

class PascalCaseName extends React.Component {
    
    render() {
        const {name, age} = this.props;
        return (
        <div>
            <h1>Hello, {name}!</h1>
            <h1>Age: {age}!</h1>
        </div>
        );
    }
}

export default PascalCaseName;
```
```javascript
//App.js
import React from 'react';
import PascalCaseName from './components/PascalCaseName/PascalCaseName';

class App extends React.Component {
    render() {
        return (
        <div className="App">
            <PascalCaseName name="name" age={20}/>
        </div>
        );
    }
}
```

## Events
```javascript
//PascalCaseName.js
import React from 'react';

class PascalCaseName extends React.Component {
    clickAlert = () => alert("Message");
    sayHello = (event, name) => alert("Hello "+ name);
    render() {
        const {name, age} = this.props;
        return (
        <div>
            <h1>Hello, {name}!</h1>
            <h1>Age: {age}!</h1>
            <button onClick={this.clickAlert}>Let's get started!</button>
            <button onClick={(e)=>this.sayHello(e, name)}>Click me!</button>
        </div>
        );
    }
}

export default PascalCaseName;
```

## State
`global variables`
we need a constructor.
```javascript
//PascalCaseName.js
import React from 'react';

class PascalCaseName extends React.Component {
    constructor(props) {
        super(props);
        this.state = {
            profession="back-end programmer";
        }
    }

    changeProfession = () => {this.state.profession}==="back-end programmer"? this.setState({profession:"front-end programmer"}): this.setState({profession:"back-end programmer"})

    clickAlert = () => alert("Message");
    sayHello = (event, name) => alert("Hello "+ name);
    render() {
        const {name, age} = this.props;
        return (
        <div>
            <h1>Hello, {name}!</h1>
            <h1>{this.state.profession} {age}!</h1>
            <button onClick={this.clickAlert}>Let's get started!</button>
            <button onClick={(e)=>this.sayHello(e, name)}>Click me!</button>
            <button onClick={this.changeProfession}>This is no my profession</button>
        </div>
        );
    }
}

export default PascalCaseName;

