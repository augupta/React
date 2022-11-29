# React
Components are one of the foundations of React
how to compose layouts by importing components into other components.
passing data from one component to another.
about JSX syntax in React and how to use it to structure and style your components.

# JavaScript Modules
function addTwo(a, b) {
    console.log(a + b);
}

# Module Exports
1.  
export default function addTwo(a, b) {
    console.log(a + b);
}
2.
function addTwo(a, b) {
    console.log(a + b);
}

export default addTwo;

# Named Exports
1.
export function addTwo(a, b) {
    console.log(a + b);
}

export function addThree(a + b + c) {
    console.log(a + b + c);
}
2.
function addTwo(a, b) {
    console.log(a + b);
}

function addThree(a + b + c) {
    console.log(a + b + c);
}

export { addTwo, addThree };

# Importing Modules
1.
import addTwo from "./addTwo";

2.
import { addTwo } from "./addTwo";


# transpiling
converting some code so that browser can comprehend or supports browser(JSX code to JS code)

# JSX Code
function Heading(props) {
    return <h1>{props.title}</h1>
}

# JS Code
function Heading(props) {
  return /*#__PURE__*/React.createElement("h1", null, props.title);
}

The first argument is the DOM element to render - in this case, an h1 element. The second property is any HTML attribute that should be added, and there's a null here - meaning, there should be an object with some data, but there isn't any data so instead of the object there's the null value. The third property is the contents of the inner HTML of the DOM element specified as the first argument - in this case, the contents of the inner HTML of the h1 element.

# Function component in App.js

function Header(){
  return <h1>hello world</h1>;
}
 function App(){
  return <Header />;
 }

 export default App;
 
 # also a valid component code
 function Example() { return (<h1>Example</h1>) }

# React folders
# node_modules
Repository for all modules of react app

# public
contains the assets that will be displayed to user in app.

# src
contains all the essential files to ensure that react app works
index.js and app.js are used to render the root components of the app.


















