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



# Building a Layout
The layout you're supposed to build will consist of the following sections:

Main navigation 
Promo (main advertisement)
A list of newest posts' previews (intros)
The footer

# Organizing Your Code

Grouping by features 
Grouping by file type 

# Building The App
1 npm init react-app customizing-example
2 Inspecting the src folder of the starter app, it looks like this:
  src/
    App.js
    App.test.js
    index.css
    index.js
    logo.svg
    reportWebVitals.js
    setupTests.js
3 Then simply add a components folder to it, like this:
  components/
4 Since the components folder is currently empty, you can add a component for each of the sections of the typography-focused blog. Here's the structural update:
  src/
    components/
        Nav.js
        Promo.js
        Intro1.js
        Intro2.js
        Intro3.js
        Footer.js
# Building Components
For now, let’s just build those components. After you've added the components folder, you’ve also added all the functional component files. Since they are all currently empty, you can start adding them, one by one.

# Discussing the Syntax
className is used in JSX to list one or more CSS classes inplace of class which is used in html to be used on a given element or component.
DRY approach - that is, the "Don't repeat yourself" approach?















