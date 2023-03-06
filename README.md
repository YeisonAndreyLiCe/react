# [React](https://es.reactjs.org/docs/getting-started.html "react documentation")

Single page application.
We can integrate it in an easy way

## components

> "A component is a piece fo UI (user Interface) that has its own logic and appearance" ([React Documentation](https://beta.es.reactjs.org/learn "learn react"))

In react components are represented as functions that return markup.

```bash
npx create-react-app {route}
cd {route}
npm start
```

## Function base component

```javascript
import React from "react";
```

## JSX

Syntax to create components
elements must be wrapping
Only one principal element

## Class based component

```javascript
//App.js
import React from "react";

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
import React from "react";

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
import React from "react";
import PascalCaseName from "./components/PascalCaseName/PascalCaseName";

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

`this.props` allow us to access the information that was passed to the component

```javascript
//PascalCaseName.js
import React from "react";

class PascalCaseName extends React.Component {
  render() {
    const { name, age } = this.props;
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
import React from "react";
import PascalCaseName from "./components/PascalCaseName/PascalCaseName";

class App extends React.Component {
  render() {
    return (
      <div className="App">
        <PascalCaseName name="name" age={20} />
      </div>
    );
  }
}
```

## Events

```javascript
//PascalCaseName.js
import React from "react";

class PascalCaseName extends React.Component {
  clickAlert = () => alert("Message");
  sayHello = (event, name) => alert("Hello " + name);
  render() {
    const { name, age } = this.props;
    return (
      <div>
        <h1>Hello, {name}!</h1>
        <h1>Age: {age}!</h1>
        <button onClick={this.clickAlert}>Let's get started!</button>
        <button onClick={(e) => this.sayHello(e, name)}>Click me!</button>
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

    changeProfession = () => {
        this.state.profession}==="back-end programmer"?
        this.setState({profession:"front-end programmer"}):
        this.setState({profession:"back-end programmer"})

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
```

## Function base component

```javascript
//PascalCaseName.js
const PascalCaseName = (props) => {
  const { name, age } = props;
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <h1>Age: {age}!</h1>
    </div>
  );
};

export default PascalCaseName;
```

## Hooks

<!-- Function that connects a part of code with a function. -->

```javascript
//PascalCaseName.js
import React, { useState } from "react";

const PascalCaseName = (props) => {
  const [profession, setProfession] = useState("back-end programmer");
  const { name, age } = props;
  const changeProfession = () => {
    profession === "back-end programmer"
      ? setProfession("front-end programmer")
      : setProfession("back-end programmer");
  };
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <h1>
        {profession} {age}!
      </h1>
      <button onClick={changeProfession}>This is no my profession</button>
    </div>
  );
};

export default PascalCaseName;
```

## Forms

```javascript
//PascalCaseName.js
import React, { useState } from "react";

const FormRegister = () => {
  return (
    <form>
      <label htmlFor="name">Name</label>
      <input type="text" id="name" />
      <label htmlFor="age">Age</label>
      <input type="number" id="age" />
      <label htmlFor="profession">Profession</label>
      <input type="text" id="profession" />
      <input type="submit" value="Register" />
    </form>
  );
};

export default FormRegister;
```

## Controlled components

```javascript
//PascalCaseName.js
import React, { useState } from "react";

const FormRegister = () => {
  const [name, setName] = useState("");
  const [age, setAge] = useState("");
  const [profession, setProfession] = useState("");
  const [submitted setSubmitted] = useState(false);
  const handleSubmit = (e) => {
    e.preventDefault();
    const newUser = {name, age, profession}
    console.log(newUser);
    //cleaning the form
    setName("");
    setAge("");
    setProfession("");
    setSubmitted(true);
  };
  
  return (
    <form onSubmit={handleSubmit}>
      <label htmlFor="name">Name</label>
      <input
        type="text"
        id="name"
        onChange={(e) => setName(e.target.value)}
        value={name}
      />
      <label htmlFor="age">Age</label>
      <input
        type="number"
        id="age"
        onChange={(e) => setAge(e.target.value)}
        value={age}
      />
      <label htmlFor="profession">Profession</label>
      <input
        type="text"
        id="profession"
        onChange={(e) => setProfession(e.target.value)}
        value={profession}
      />
      <input type="submit" value="Register" />
    </form>

    {submitted && <div>
        <h2>Thank you for registering!</h2>
    </div>}
  );
};
```
