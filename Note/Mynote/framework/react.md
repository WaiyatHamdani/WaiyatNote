
## Table of Contents
- [Basic Functional Component](#basic-functional-component)
- [Controlled Components](#controlled-components)
- [Use Hook](#use-hook)
  - [useState](#use-state)
  - [useEffect](#use-effect)
  - [useContext](#use-context)
- [Axios](#axios)
- [Router](#router)
- [Map Looping](#map-looping)

## Basic Functional Component

```tsx
import React from 'react';

function MyComponent (){
  return (
    <div>
      <h1>Hello, World!</h1>
    </div>
  );
};

export default MyComponent;
```

### Controlled Components
```tsx
    const [text, setText] = useState('');
    function handleSubmit(e){
        e.preventDefault(); // Prevent the default form submission
        alert(`You entered: ${text}`);
    };

    return (
        <form onSubmit={handleSubmit}>
            <input type="text"
                    value={text}
                    onChange={(e) => setText(e.target.value)}
            />
            <button type="submit">Submit</button>
        </form>
    );
```

## Use Hook
### Use State 
```tsx
function NameInput(){
  const [name, setName] = useState<string | null >('');  // setting the useState

  return (
            <div>
                <form>
                    <label>Enter your name:</label>
                    <input type="text" 
                            value={name} 
                            onChange={(e) => setName(e.target.value)} // Update state on change
                    />
        
                </form>
                <p>Your name is: {name}</p>
            </div>
  );
};
export default NameInput;
```

### Use Effect
basic syntax
```tsx
useEffect(() => {
}, []); 
```
how to use it 
```tsx
import React, { useState, useEffect } from 'react';

function home(){
    const [userData, setUserData] = useState<users | null>(null);
    useEffect(() => {
        async function fetchCurrentUser() {
          try{
            const response = await axios.get(userUrl);
            setUserData(response.data);
          }catch(error){
            console.error('Error fetching user data:', error);
          }
        }

  fetchCurrentUser() // we need to call the fucntion again 

  }, []); // Empty dependency array means this effect runs once when the component mounts

return(<div></div>)
}

export default TimerComponent;
```

### Use Context
```tsx
  import React, { useContext } from 'react';

// Create a Context
const ThemeContext = React.createContext('light');

function ThemeDisplay() {
    const theme = useContext(ThemeContext); // Access the theme value from the context

    return <p>The current theme is {theme}</p>;
}

export default function App() {
  return (
    <ThemeContext.Provider value="dark">
      <ThemeDisplay />
    </ThemeContext.Provider>
  );
}
```

## Axios
```tsx
// GET request
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
        console.log(response.data); // Logs the array of posts
        //or
        const response = await axios.get('https://api.example.com/data', {
            headers: {
              'Accept': 'application/json',
            },
        });

//POST Request
        const requestBody = {
          key: 'value',
        };

        const response = await axios.post('https://api.example.com/users', requestBody, {
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json',
        },
        });

//PUT Request 
        const requestBody = {
          name: 'John Doe',
          email: 'johndoe@example.com',
        };

        const response = await axios.put(`https://api.example.com/users/${userId}`, requestBody, {
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json',
          },
        });        

//PATCH Request
        const requestBody = {
          email: 'newemail@example.com',
        };

        const response = await axios.patch(`https://api.example.com/users/${userId}`, requestBody, {
          headers: {
            'Content-Type': 'application/json',
            'Accept': 'application/json',
          },
        });
```

### Map Looping
```tsx
  import React from 'react';

  function ItemList() {
      const items = ['kunai', 'shuriken', 'katana', 'bow'];

      return (
        <ul>
          {items.map((item, index) => (
            <li key={index}>{item}</li> // for each element
          ))}
        </ul>
      );
  }

export default ItemList;
```

### Router
npm install react-router-dom
```tsx
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/home" component={Home} />
        <Route path="/about" component={About} />
      </Switch>
    </Router>
  );
}
```