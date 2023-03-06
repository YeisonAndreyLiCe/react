# [React](https://es.reactjs.org/docs/getting-started.html "react documentation")

Single page application.

<!-- We can integrate it in an easy way -->

## installation

```bash
npx create-react-app {route}
cd {route}
npm start
```

## components

> "A component is a piece fo UI (user Interface) that has its own logic and appearance" ([React Documentation](https://beta.es.reactjs.org/learn "learn react"))

In react components are represented as functions that return markup.

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

When creating components we will use PascalCase structure, that aiming to differentiate between HTML and react components.

```bash
cd src
mkdir components
mkdir User
cd User
touch User.js
```

```javascript
//User.js
import React from "react";

class User extends React.Component {
  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
      </div>
    );
  }
}

export default User;
```

```javascript
//App.js
import React from "react";
import User from "./components/User/User";

class App extends React.Component {
  render() {
    return (
      <div className="App">
        <User />
      </div>
    );
  }
}
```

## Props

`this.props` allow us to access the information that was passed to the component. In this case I will use information provided by [{JSON} Placeholder](https://jsonplaceholder.typicode.com "jsonplaceholder"). Here an example of the info we will obtain from this API:

```json
{
  "id": 1,
  "name": "Leanne Graham",
  "username": "Bret",
  "email": "Sincere@april.biz",
  "address": {
    "street": "Kulas Light",
    "suite": "Apt. 556",
    "city": "Gwenborough",
    "zipcode": "92998-3874",
    "geo": {
      "lat": "-37.3159",
      "lng": "81.1496"
    }
  },
  "phone": "1-770-736-8031 x56442",
  "website": "hildegard.org",
  "company": {
    "name": "Romaguera-Crona",
    "catchPhrase": "Multi-layered client-server neural-net",
    "bs": "harness real-time e-markets"
  }
}
```

I also will use [bootstrap](https://getbootstrap.com "bootstrap") to give style to the components.

```javascript
//User.js
import React from "react";

class User extends React.Component {
  render() {
    const { name, username, email, address, phone, website, company } =
      this.props;
    return (
      <div className="container">
        <h1>Hello, {name}!</h1>
        <p>This is the information your information</p>
        <ul className="list-group">
          <li className="list-group-item">{username}</li>
          <li className="list-group-item">{email}</li>
          <li className="list-group-item">{address.street}</li>
          <li className="list-group-item">{phone}</li>
          <li className="list-group-item">{website}</li>
          <li className="list-group-item">{company.name}</li>
        </ul>
      </div>
    );
  }
}

export default User;
```

```javascript
//App.js
import React from "react";
import User from "./components/User/User";

class App extends React.Component {
  render() {
    return (
      <div className="App">
        <User
          name="Leanne Graham"
          username="Bret"
          email="leann@gmai.com"
          address={{
            street: "Kulas Light",
            suite: "Apt. 556",
            city: "Gwenborough",
            zipcode: "92998-3874",
            geo: {
              lat: "-37.3159",
              lng: "81.1496",
            },
          }}
          phone="1-770-736-8031 x56442"
          website="hildegard.org"
          company={{
            name: "Romaguera-Crona",
            catchPhrase: "Multi-layered client-server neural-net",
            bs: "harness real-time e-markets",
          }}
        />
      </div>
    );
  }
}
```

## Events

```javascript
//PascalCaseName.js
import React from "react";

class User extends React.Component {
  clickAlert = () => alert("Happy hacking!");
  sayHello = (event, name) =>
    alert("Sorry " + name + "that's no possible, not yet!");
  render() {
    const { name, username, email, address, phone, website, company } =
      this.props;
    return (
      <div className="container">
        <h1>Hello, {name}!</h1>
        <p>This is the information your information</p>
        <ul className="list-group">
          <li className="list-group-item">{username}</li>
          <li className="list-group-item">{email}</li>
          <li className="list-group-item">{address.street}</li>
          <li className="list-group-item">{phone}</li>
          <li className="list-group-item">{website}</li>
          <li className="list-group-item">{company.name}</li>
        </ul>
        <button className="btn btn-success" onClick={this.clickAlert}>
          That's Right!
        </button>
        <button
          className="btn btn-danger"
          onClick={(e) => this.sayHello(e, name)}
        >
          I wanna change the info!
        </button>
      </div>
    );
  }
}

export default User;
```

## State

`global variables` we need a constructor in the case of class based components.

```javascript
//User.js
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
        const { name, username, email, address, phone, website, company, profession} = this.props;
      return (
        <div className="container">
          <h1>Hello, {name}!</h1>
          <p>This is the information your information</p>
          <ul className="list-group">
            <li className="list-group-item">{username}</li>
            <li className="list-group-item">{email}</li>
            <li className="list-group-item">{address.street}</li>
            <li className="list-group-item">{phone}</li>
            <li className="list-group-item">{website}</li>
            <li className="list-group-item">{company.name}</li>
            <li className="list-group-item">{profession}</li>
          </ul>
          <div class="d-grid gap-2">
            <button className="btn btn-success" onClick={this.clickAlert}>That's Right!</button>
            <button className="btn btn-danger" onClick={(e) => this.sayHello(e, name)}>I wanna change the info!</button>
            <button onClick={this.changeProfession}>That's is no my profession!</button>
          </div>
        </div>
        );
    }
}

export default User;
```

---

## Function base component

```javascript
//User.js
const User = (props) => {
  const {
    name,
    username,
    email,
    address,
    phone,
    website,
    company,
    profession,
  } = props;
  return (
    <div className="container">
      <h1>Hello, {name}!</h1>
      <p>This is the information your information</p>
      <ul className="list-group">
        <li className="list-group-item">{username}</li>
        <li className="list-group-item">{email}</li>
        <li className="list-group-item">{address.street}</li>
        <li className="list-group-item">{phone}</li>
        <li className="list-group-item">{website}</li>
        <li className="list-group-item">{company.name}</li>
        <li className="list-group-item">{profession}</li>
      </ul>
    </div>
  );
};

export default User;
```

## Hooks

<!-- Function that connects a part of code with a function. -->

```javascript
//User.js
import React, { useState } from "react";

const User = (props) => {
  const [profession, setProfession] = useState("back-end programmer");
  const {
    name,
    username,
    email,
    address,
    phone,
    website,
    company,
    profession,
  } = props;
  const changeProfession = () => {
    profession === "back-end programmer"
      ? setProfession("front-end programmer")
      : setProfession("back-end programmer");
  };
  return (
    <div className="container">
      <h1>Hello, {name}!</h1>
      <p>This is the information your information</p>
      <ul className="list-group">
        <li className="list-group-item">{username}</li>
        <li className="list-group-item">{email}</li>
        <li className="list-group-item">{address.street}</li>
        <li className="list-group-item">{phone}</li>
        <li className="list-group-item">{website}</li>
        <li className="list-group-item">{company.name}</li>
        <li className="list-group-item">{profession}</li>
      </ul>
      <div class="d-grid gap-2">
        <button className="btn btn-danger" onClick={changeProfession}>
          That's is no my profession!
        </button>
      </div>
    </div>
  );
};

export default User;
```

## Forms

```javascript
//User.js
import React, { useState } from "react";

const FormRegister = () => {
  return (
    <form>
      <div class="mb-3">
        <label htmlFor="name" className="form-label">
          Full Name
        </label>
        <input type="text" className="form-control" id="name" />
      </div>
      <div class="mb-3">
        <label htmlFor="email" className="form-label">
          Email address
        </label>
        <input
          type="email"
          className="form-control"
          id="email"
          aria-describedby="emailHelp"
        />
        <div id="emailHelp" className="form-text">
          We'll never share your email with anyone else.
        </div>
      </div>
      <div class="mb-3">
        <p> Address </p>
        <label htmlFor="street" className="form-label">
          street
        </label>
        <input type="text" className="form-control" id="street" />
        <label htmlFor="suite" className="form-label">
          suite
        </label>
        <input type="text" className="form-control" id="suite" />
        <label htmlFor="city" className="form-label">
          city
        </label>
        <input type="text" className="form-control" id="city" />
        <label htmlFor="zipcode" className="form-label">
          zipcode
        </label>
        <input type="text" className="form-control" id="zipcode" />
      </div>
      <div class="mb-3">
        <label htmlFor="phone" className="form-label">
          Phone
        </label>
        <input type="text" className="form-control" id="phone" />
      </div>
      <div class="mb-3">
        <label htmlFor="website" className="form-label">
          Website
        </label>
        <input type="text" className="form-control" id="website" />
      </div>
      <div class="mb-3">
        <p> Company </p>
        <label htmlFor="companyName" className="form-label">
          Company Name
        </label>
        <input type="text" className="form-control" id="companyName" />
        <label htmlFor="catchPhrase" className="form-label">
          Catch Phrase
        </label>
        <input type="text" className="form-control" id="catchPhrase" />
        <label htmlFor="bs" className="form-label">
          bs
        </label>
        <input type="text" className="form-control" id="bs" />
      </div>
      <div class="mb-3">
        <label htmlFor="profession" className="form-label">
          Profession
        </label>
        <input type="text" className="form-control" id="profession" />
      </div>
      <button type="submit" className="btn btn-primary">
        Submit
      </button>
    </form>
  );
};

export default FormRegister;
```

## Controlled components

```javascript
//FormRegister.js
import React, { useState } from "react";

const FormRegister = () => {
  const [name, setName] = useState("");
  const [username, setUsername] = useState("");
  const [email, setEmail] = useState("");
  const [street, setStreet] = useState("");
  const [suite, setSuite] = useState("");
  const [city, setCity] = useState("");
  const [zipcode, setZipcode] = useState("");
  const [phone, setPhone] = useState("");
  const [website, setWebsite] = useState("");
  const [companyName, setCompanyName] = useState("");
  const [profession, setProfession] = useState("");
  const [submitted setSubmitted] = useState(false);
  const handleSubmit = (e) => {
    e.preventDefault();
    const newUser = { name, username, email, address: {street, suite, city, zipcode}, phone, website, companyName, profession}
    console.log(newUser);
    //cleaning the form
    setName("");
    setUsername("");
    setEmail("");
    setStreet("");
    setSuite("");
    setCity("");
    setZipcode("");
    setPhone("");
    setWebsite("");
    setCompanyName("");
    setProfession("");
    setSubmitted(true);
  };

  return (
    <form onSubmit={handleSubmit} className="form-group">
      <div class="mb-3">
        <label htmlFor="name" className="form-label">Full Name</label>
        <input type="text" className="form-control" id="name" value={name} onChange={(e) => setName(e.target.value)} />
      </div>
      <div class="mb-3">
        <label htmlFor="username" className="form-label">Username</label>
        <input type="text" className="form-control" id="username" value={username} onChange={(e) => setUsername(e.target.value)} />
      </div>
      <div class="mb-3">
        <label htmlFor="email" className="form-label">Email address</label>
        <input type="email" className="form-control" id="email" aria-describedby="emailHelp" value={email} onChange={(e) => setEmail(e.target.value)} />
        <div id="emailHelp" className="form-text">We'll never share your email with anyone else.</div>
      </div>
      <div class="mb-3">
        <p> Address </p>
        <label htmlFor="street" className="form-label">street</label>
        <input type="text" className="form-control" id="street" value={street} onChange={(e) => setStreet(e.target.value)} />
        <label htmlFor="suite" className="form-label">suite</label>
        <input type="text" className="form-control" id="suite" value={suite} onChange={(e) => setSuite(e.target.value)} />
        <label htmlFor="city" className="form-label">city</label>
        <input type="text" className="form-control" id="city" value={city} onChange={(e) => setCity(e.target.value)} />
        <label htmlFor="zipcode" className="form-label">zipcode</label>
        <input type="text" className="form-control" id="zipcode" value={zipcode} onChange={(e) => setZipcode(e.target.value)} />
      </div>
      <div class="mb-3">
        <label htmlFor="phone" className="form-label">Phone</label>
        <input type="text" className="form-control" id="phone" value={phone} onChange={(e) => setPhone(e.target.value)} />
      </div>
      <div class="mb-3">
        <label htmlFor="website" className="form-label">Website</label>
        <input type="text" className="form-control" id="website" value={website} onChange={(e) => setWebsite(e.target.value)} />
      </div>
      <div class="mb-3">
        <p> Company </p>
        <label htmlFor="companyName" className="form-label">Company Name</label>
        <input type="text" className="form-control" id="companyName" value={companyName} onChange={(e) => setCompanyName(e.target.value)} />
        <label htmlFor="catchPhrase" className="form-label">Catch Phrase</label>
        <input type="text" className="form-control" id="catchPhrase" value={catchPhrase} onChange={(e) => setCatchPhrase(e.target.value)} />
        <label htmlFor="bs" className="form-label">bs</label>
        <input type="text" className="form-control" id="bs" value={bs} onChange={(e) => setBs(e.target.value)} />
      </div>
      <div class="mb-3">
        <label htmlFor="profession" className="form-label">Profession</label>
        <input type="text" className="form-control" id="profession" value={profession} onChange={(e) => setProfession(e.target.value)} />
      </div>
      <button type="submit" className="btn btn-primary">Submit</button>
    </form>

    {submitted && <div>
        <h2>Thank you for registering!</h2>
    </div>}
  );
};

export default FormRegister;
```

## Mapping Objects

```javascript
//App.js
import React, { useState } from "react";
import FormRegister from "./components/FormRegister/FormRegister";
import User from "./components/User/User";

const APP = () => {
  const [users, setUsers] = useState([]);
  const addUser = (user) => {
    setUsers([...users, user]);
  };
  return (
    <div className="App">
      <FormRegister />
      <div>
        {users.map((user, index) => (
          <div key={index}>
            <User
              name={user.name}
              username={user.username}
              email={user.email}
              address={user.address}
              phone={user.phone}
              website={user.website}
              companyName={user.companyName}
              profession={user.profession}
            />
          </div>
        ))}
      </div>
    </div>
  );
};

export default APP;
```

## Use Effect

Generally use to call APIs

```javascript
//App.js
import React, { useState, useEffect } from "react";
import FormRegister from "./components/FormRegister/FormRegister";
import User from "./components/User/User";

const APP = () => {
  const [users, setUsers] = useState([]);
  const addUser = (user) => {
    setUsers([...users, user]);
  };
  useEffect(() => {
    console.log("useEffect");
  }, [users]);
  return (
    <div className="App">
      <FormRegister />
      <div>
        {users.map((user, index) => (
          <div key={index}>
            <User
              name={user.name}
              username={user.username}
              email={user.email}
              address={user.address}
              phone={user.phone}
              website={user.website}
              companyName={user.companyName}
              profession={user.profession}
            />
          </div>
        ))}
      </div>
    </div>
  );
};

export default APP;
```

## Use Effect with API

```javascript
//App.js
import React, { useState, useEffect } from "react";
import FormRegister from "./components/FormRegister/FormRegister";
import User from "./components/User/User";

const APP = () => {
  const [users, setUsers] = useState([]);
  const addUser = (user) => {
    setUsers([...users, user]);
  };
  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => setUsers(data));
  }, []);
  return (
    <div className="App">
      <FormRegister />
      <div>
        {users.map((user, index) => (
          <div key={index}>
            <User
              name={user.name}
              username={user.username}
              email={user.email}
              address={user.address}
              phone={user.phone}
              website={user.website}
              companyName={user.companyName}
              profession={user.profession}
            />
          </div>
        ))}
      </div>
    </div>
  );
};

export default APP;
```

## Use Effect with API and conditional rendering

```javascript
//App.js
import React, { useState, useEffect } from "react";
import FormRegister from "./components/FormRegister/FormRegister";
import User from "./components/User/User";

const APP = () => {
  const [users, setUsers] = useState([]);
  const addUser = (user) => {
    setUsers([...users, user]);
  };
  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => setUsers(data));
  }, []);
  return (
    <div className="App">
      <FormRegister />
      <div>
        {users.length > 0 ? (
          users.map((user, index) => (
            <div key={index}>
              <User
                name={user.name}
                username={user.username}
                email={user.email}
                address={user.address}
                phone={user.phone}
                website={user.website}
                companyName={user.companyName}
                profession={user.profession}
              />
            </div>
          ))
        ) : (
          <h1>Loading...</h1>
        )}
      </div>
    </div>
  );
};

export default APP;
```

## [Axios](https://axios-http.com/docs/intro "Axios doc")

Library to use APIs

```bash
npm install axios
```

```javascript
//App.js
import React, { useState, useEffect } from "react";
import FormRegister from "./components/FormRegister/FormRegister";
import User from "./components/User/User";
import axios from "axios";

const APP = () => {
  const [users, setUsers] = useState([]);
  const addUser = (user) => {
    setUsers([...users, user]);
  };
  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => setUsers(response.data));
  }, []);
  return (
    <div className="App">
      <FormRegister />
      <div>
        {users.length > 0 ? (
          users.map((user, index) => (
            <div key={index}>
              <User
                name={user.name}
                username={user.username}
                email={user.email}
                address={user.address}
                phone={user.phone}
                website={user.website}
                companyName={user.companyName}
                profession={user.profession}
              />
            </div>
          ))
        ) : (
          <h1>Loading...</h1>
        )}
      </div>
    </div>
  );
};

export default APP;
```

## React Router

```bash
npm install react-router-dom
```

```javascript
//App.js
import React, { useState, useEffect } from "react";
import FormRegister from "./components/FormRegister/FormRegister";
import User from "./components/User/User";
import axios from "axios";
import { BrowserRouter as Router, Switch, Route, Link } from "react-router-dom";

const APP = () => {
  const [users, setUsers] = useState([]);
  const addUser = (user) => {
    setUsers([...users, user]);
  };
  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then((response) => setUsers(response.data));
  }, []);
  return (
    <Router>
      <div className="App">
        <FormRegister />
        <div>
          {users.length > 0 ? (
            users.map((user, index) => (
              <div key={index}>
                <User
                  name={user.name}
                  username={user.username}
                  email={user.email}
                  address={user.address}
                  phone={user.phone}
                  website={user.website}
                  companyName={user.companyName}
                  profession={user.profession}
                />
              </div>
            ))
          ) : (
            <h1>Loading...</h1>
          )}
        </div>
      </div>
    </Router>
  );
};

export default APP;
```
