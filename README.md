# to check node and npm versions in terminal
node -v
npm -v

# Mac terminal commands

# Basics
/ (Forward Slash). Top level directory
. (Single Period)  Current directory
.. (Double Period)  Parent directory
~ (Tilde). Home directory
sudo [command]  Run command with the security privileges of the super user
nano [file]. Opens the Terminal editor
open [file]. Opens a file
[command] -h  Get help about a command
man [command]. Show the help manual of the command

# Change Directory

cd  Home directory
cd [folder]  Change directory, e.g. cd Documents
cd ~  Home directory
cd/  Root of the drive
cd -  Previous directory or folder you last browsed
pwd  Show your working directory
cd..  Move up to the parent directory
cd../..  Move up two levels
 

# cd..  to move a folder back in terminal
# cd folder name   to move to the mentioned folder

# creating a new react app :  npx create-react-app my_app  
  cd my_app
  npm start : to see local host server
  npm run build : for optimization, it converts all files into one file which is better for users
  
# npm init react-app my-app  (the correct command to build a starter React app to work off of.) 
# ./ to go inside folder
# ../ to go out folder
# ../../ to go out of directory


# React Concepts
- DOM Manipulation
- Reusable Components
- Unidirectional Flow
- UI, rest, u can add other libraries 

#
Decide on Components.
Decide the state and where it lives.
What changes when state changes.

# NPM vs Yarn
Install dependencies from package.json: npm install == yarn
Install a package and add to package.json: npm install package -save == yarn add package
Install a devDependency to package.json: npm install package -save-dev == yarn add package-dev
Remove a dependency from package.json: npm uninstall package-save == yarn remove package
Upgrade a package to its latest version: npm update-save == yarn upgrade
Install a package globally: npm install package -g== yarn global add package

# npx vs npm
npm- install packages and execute 
npx- execute without installing


# React lets you create components, reusable UI elements for your app.

In a React app, every piece of UI is a component.

React components are regular JavaScript functions except:

Their names always begin with a capital letter.
They return JSX markup.


# 🔴 Never define a component inside another component! 
export default function Gallery() {
  function Profile() {
    // ...
  }
  // ...
}

# The snippet above is very slow and causes bugs. Instead, define every component at the top level:
export default function Gallery() {
  // ...
}

// ✅ Declare components at the top level
function Profile() {
  // ...
}

# When a child component needs some data from a parent, pass it by props instead of nesting definitions.

# How you export your component dictates how you must import it. You will get an error if you try to import a default export the same way you would a named export! This chart can help you keep track:

Syntax	Export statement	Import statement:
Default:	export default function Button() {}	-> import Button from './Button.js';
Named:	export function Button() {}	 ->   import { Button } from './Button.js';

#  A file can only have one default export, but it can have numerous named exports!
# A component must be pure, meaning:
# It minds its own business. It should not change any objects or variables that existed before rendering.
# Same inputs, same output. Given the same inputs, a component should always return the same JSX.
# Rendering can happen at any time, so components should not depend on each others’ rendering sequence.
# You should not mutate any of the inputs that your components use for rendering. That includes props, state, and context. To update the screen, “set” state instead of mutating preexisting objects. Pure functions don’t mutate variables outside of the function’s scope or objects that were created before the call—that makes them impure! it’s completely fine to change variables and objects that you’ve just created while rendering. 
# Wrong Practice
let guest = 0;

function Cup() {
  // Bad: changing a preexisting variable!
  guest = guest + 1;
  return <h2>Tea cup for guest #{guest}</h2>;
}

export default function TeaSet() {
  return (
    <>
      <Cup />
      <Cup />
      <Cup />
    </>
  );
}

# Right Practice
function Cup({ guest }) {
  return <h2>Tea cup for guest #{guest}</h2>;
}

export default function TeaGathering() {
  let cups = [];
  for (let i = 1; i <= 12; i++) {
    cups.push(<Cup key={i} guest={i} />);
  }
  return cups;
}

# Strive to express your component’s logic in the JSX you return. When you need to “change things”, you’ll usually want to do it in an event handler. As a last resort, you can useEffect.
# Writing pure functions takes a bit of practice, but it unlocks the power of React’s paradigm.

# Adding event handlers 
1. To add an event handler, you will first define a function and then pass it as a prop to the appropriate JSX tag.
2. Declare a function called handleClick inside your Button component.
3. Implement the logic inside that function (use alert to show the message).
4. Add onClick={handleClick} to the <button> JSX.

export default function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>
      Click me
    </button>
  );
}

# Alternatively, you can define an event handler inline in the JSX:

<button onClick={function handleClick() {
  alert('You clicked me!');
}}>
Or, more concisely, using an arrow function:

<button onClick={() => {
  alert('You clicked me!');
}}>

# Functions passed to event handlers must be passed, not called. For example:
passing a function (correct)	calling a function (incorrect)
<button onClick={handleClick}>	<button onClick={handleClick()}>

The difference is subtle. In the first example, the handleClick function is passed as an onClick event handler. This tells React to remember it and only call your function when the user clicks the button.

In the second example, the () at the end of handleClick() fires the function immediately during rendering, without any clicks. This is because JavaScript inside the JSX { and } executes right away. 
 
 
# functional components vs class components  
functional components- stateless prev, now can write with state also, componentdidmount doesnt work, can use props, no use of render method, 
class components - statefull, make use of ES6 class, extends, can use state & props, and lifecycle methods, use render(){}
                   under class components functions will be written as functionName(){} 

# Modern way of writing React : Functions with Hooks : function(props, state){}
# Older way : Class

# whenever using {} under return statement, it means bracket needs jsx variable which could be EX: this.state.name 

# Passing Props to a Component
React components use props to communicate with each other. Every parent component can pass some information to its child components by giving them props. Props might remind you of HTML attributes, but you can pass any JavaScript value through them, including objects, arrays, and functions.

# props vs state
props get passed to component
props are immutable
props.name in functional components
prpos moves parent to child(downwards)
You can’t change props. When you need interactivity, you’ll need to set state.


state is managed within a component
we use state when we want something to change or our react function suppose to give different UI and this happens with the helps of hooks
bcoz local variable(inside function) cant update for that we need hooks
state can never be used directly, always use inside the setter
states can be changed
states can be used in functional components
this.props.name in class components
state gets updated asynchonously, that means after func gets run then react decided to update state
whenever state gets updated, function renders again
state moves from child to parent or child to sibling


# Where to get your key 
Different sources of data provide different sources of keys:
Data from a database: If your data is coming from a database, you can use the database keys/IDs, which are unique by nature.
Locally generated data: If your data is generated and persisted locally (e.g. notes in a note-taking app), use an incrementing counter, crypto.randomUUID() or a package like uuid when creating items.

# Rules of keys 
Keys must be unique among siblings. However, it’s okay to use the same keys for JSX nodes in different arrays.
Keys must not change or that defeats their purpose! Don’t generate them while rendering.
# Why does React need keys? 

Imagine that files on your desktop didn’t have names. Instead, you’d refer to them by their order — the first file, the second file, and so on. You could get used to it, but once you delete a file, it would get confusing. The second file would become the first file, the third file would be the second file, and so on.
File names in a folder and JSX keys in an array serve a similar purpose. They let us uniquely identify an item between its siblings. A well-chosen key provides more information than the position within the array. Even if the position changes due to reordering, the key lets React identify the item throughout its lifetime.

# eventHandling - in eventHandling dont call function inside jsx {},means dont use parenthesis, just write function name without bracets
for class components <button onClick={this.changeEvent}>Click me</button>
for functional Components <button onClick={changeEvent}>Click me</button>

# Use of Fragment:
Fragment used to eliminate div tag in return when there are multiple tags

# Normal Function gives output and react function gives UI

#
// ReactDOM.render(
//     <div>
//         <h1>Heading1</h1>
//         <p>This is paragraph</p>
//     </div>,
//     document.getElementById("root"));



// const page=(<div>
//     <h1>Heading1</h1>
//     <p>This is paragraph</p>
//     <NavBar />
//     <MainContent />
//     </div>
// );
// ReactDOM.render(
//     page,
//     document.getElementById("root")
// );



// function NavBar(){
//     return(
//         <button className="navButton" type="submit">Signup</button>
//     )
// }
// function MainContent(){
//     return(
//         <p>Hello</p>
//     )
// }
// ReactDOM.render(
//     <div>
//         <h1>Heading1</h1>
//         <p>This is paragraph</p>
//         <NavBar />
//         <MainContent />
//     </div>,
//     document.getElementById("root"));


// when there is no cdm
// import React from 'react';
// import ReactDOM from 'react-dom';

function Header(){
    return(
        <div>
            <nav className='nav'>
                <img src= "../html_css/binance.jpg" width="40px">
                </img>
                <ul className='navList'>
                    <li>Home</li>
                    <li>About</li>
                    <li>Contact</li>
                </ul>
            </nav>
        </div>
    );
}
function Main(){
    return(
        <div>
            <h1>Fun facts about React</h1>
            <ul>
                <li>unordered list items</li>
                <li>unordered list items</li>
                <li>unordered list items</li>
                <li>unordered list items</li>
            </ul>
        </div>
    );
}
function Page(){
    return(
        <div>
            <Header />
            <Main /> 
        </div>
    )
    
}

ReactDOM.render(
<Page />,
document.getElementById("root"));




# React app structure 
The top level directory structure will be as follows:

assets - global static assets such as images, svgs, company logo, etc.
components - global shared/reusable components, such as layout (wrappers, navigation), form components, buttons
services - JavaScript modules
store - Global Redux store
utils - Utilities, helpers, constants, and the like
views - Can also be called "pages", the majority of the app would be contained here

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
# Default Export (when function name is same as file name)
1.  
export default function addTwo(a, b) {
    console.log(a + b);
}
2.
function addTwo(a, b) {
    console.log(a + b);
}

export default addTwo;
 
# Named Export(when function name is different from file name)
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

function App() {
  return (
    <div>
    <h1>Hello there</h1> 
    </div>
  )
}

# JS Code
function Heading(props) {
  return /*#__PURE__*/React.createElement("h1", null/{}, props.title);
}

function App() {
  return /*#__PURE__*/React.createElement("div", null/{}, /*#__PURE__*/React.createElement("h1", null/{}, "Hello there"));
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
1 npm init react-app customizing-example   (the correct command to build a starter React app to work off of.) 
OR 
create-react-app customizing-example   (What is create-react-app? It’s an npm package used to build a boilerplate React app.)

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

Recall that much like parameters in a JavaScript function which allow you to pass in values as arguments, React uses properties, or props, to pass data between components. 

# Props and children
props are immutable

function Apples(props) {
  return (
    <div className="promo-section">
        <div>
            <h2>These apples are: {props.color}</h2>
            </div>
            <div>
            <h3>There are {props.number} apples.</h3>
        </div>
    </div>
  )
}
export default Apples

function Pears(props) {
  return (
    <h2>I don't like pears, but my friend, {props.friend}, does</h2>
  )
}
export default Pears

function Bag(props) {
    const bag = {
        maxHeight: "200px",
        backgroundColor: "rgb(21, 21, 25)",
        color: "whitesmoke",
        display: "flex",
        flexDirection: "row",
        justifyContent: "space-between"
    }
    return (
        <div style={bag}>
            {props.children}
        </div>
    )
}
export default Bag

<Bag children={<Apples color="yellow" number="5" />} />
<Bag children={<Pears friend="Peter" />} />

Effectively, the above syntax is the same as the two examples below.
 
<Bag>
    <Apples color="yellow" number="5" />
</Bag>

<Bag>
    <Pears friend="Peter" />
</Bag>

In the above code, Apples is a prop of the Bag component

# Styling JSX elements
# In CSS:
.promo-section {
    font-weight: bold;
    line-height: 20px;
}
# 
function Promo(props) {
    return (
        <div className="promo-section">
            <div>
                <h1 style={{color:"tomato", fontSize:"40px", fontWeight:"bold"}}>
                    {props.heading}
                </h1>
            </div>
            <div>
                <h2>{props.promoSubHeading}</h2>
            </div>
        </div>
    );
}

export default Promo;
#
function Promo(props) {

const styles = {
    color: "tomato",
    fontSize: "40px"
}

return (
        <div className="promo-section">
            <div>
                <h1 style={styles}>
                    {props.heading}
                </h1>
            </div>
            <div>
                <h2>{props.promoSubHeading}</h2>
            </div>
        </div>
    );
}

#
export default function Nav(){
    const navStyle={
        body:{
            maxHeight: "200px",
            backgroundColor: "rgb(21, 21, 25)",
            color: "cyan",
            display: "flex",
            flexDirection: "row",
            justifyContent: "space-between",
        },
        imgBar:{
            display: "flex",
            flexDirection: "row"
        }
    }
    return(
        <nav style={navStyle.body} className="navBar">
            <div style={navStyle.imgBar} className= "imgBar">
                <img src= "../../../html_css/binance.jpg"></img>
                <h2>React Facts</h2>
            </div>
            <h4>React Course- Project-1</h4>
        </nav>
    )
}

# arrow function
When an arrow function has a single parameter, you do not need to add parentheses around the item parameter (to the left of the arrow).
function(item) {
    return item * 10
}
OR
item => item * 10

# Expressions in HTML Attributes
const url= "photo.png";
const result= <img src= {url}></img>;

# Ternary operators and functions in JSX
let name = 'Bob';
if (name == 'Bob') {
    console.log('Hello, Bob');
} else {
    console.log('Hello, Friend');
};
OR
let name = 'Bob';
name == 'Bob' ? console.log('Hello, Bob') : console.log('Hello, Friend');

# Using ternary expressions in JSX

function Example() {
    return (
        <div className="heading">
            <h1>{Math.random() => 0.5 ? "Over 0.5" : "Under 0.5"}</h1>
        </div>
    );
};

function Example3() {

    const getRandomNum = () => Math.floor(Math.random() * 10) + 1

    return (
        <div className="heading">
            <h1>Here's a random number from 0 to 10: { getRandomNum() }</h1>
        </div>
    );
};

# when function has a name and not assigned to any variable called function Attribute and when function doesnt has a name and assigned to variable called function Expression

# div is element

# Event handling and embedded expressions
# Handling events using inline anonymous ES5 functions
<button onClick={function() {console.log('first example')}}>
    An inline anonymous ES5 function event handler
</button>

# Handling events using inline anonymous ES6 functions (arrow functions)
<button onClick={() => console.log('second example')}>
    An inline anonymous ES6 function event handler
</button>

# Handling events using separate function declarations
function App() {
    function thirdExample() {
        console.log('third example');
    };
    return (
        <div className="thirdExample">
            <button onClick={thirdExample}>
                using a separate function declaration
            </button>
        </div>
    );
};
export default App;

# Handling events using separate function expressions
function App() {
    const fourthExample = () => console.log('fourth example');

    return (
        <div className="fourthExample">
            <button onClick={fourthExample}>
                using a separate function expression
            </button>
        </div>
  );
};
export default App;


# Parent-child data flow (Props are immutable (cannot be changed).)
# Parent component:
function Dog() {
    return (
        <Puppy name="Max" bowlShape="square" bowlStatus="full" />
    );
};

# Child component:
function Puppy(props) {
    return (
        <div>
            {props.name} has <Bowl bowlShape="square" bowlStatus="full" />
        </div>
    );
};

# Grandchild component:
function Bowl(props) {
    return (
        <span>
            {props.bowlShape}-shaped bowl, and it's currently {props.bowlStatus}
        </span>
    );
};

# Updating multiple components mul times by updating just one Object
const data = { heading: "50% off on all items", callToAction: "Everything must go!" };

function promo(){
    return (<div>
        <promoHeading heading={data.heading} callToAction={data.callToAction} />
    </div>)
};

function promoHeading(props) {
    return (
        <h1>{props.heading}</h1>
        <h2>{props.callToAction}</h2>
    )
};


# Data - 1.Props  2.State
State data is a component’s internal data, which it can control and mutate. Props data is outside of the component and is immutable, meaning it cannot change.

# Hooks
importReact, {useState} from 'react';

// declaring a state variable
const[state, setState]= useState(initialState);

// Array destructuring
// useState hook should be use at the top level of ur component
// useState can be used to track any kind of DataTransfer(strings, arrays, obj, booleans etc)
// readability and simplicity to the code are the biggest benefits of hooks

# State
# Statefull(with a hook)<-> Stateless
function App() {
  const [word, setWord] = React.useState('eat')
  return (<div>
    <Heading message= {word + " at little lema Restobar"} />
  </div>)
};

# what if u want to update word 'eat' to 'drink'
function App() {
  const [word, setWord] = React.useState('eat');
  const clickHandler = () => setWord('drink');
  // function clickHandler() { setWord('drink') };
  return (<div>
    <Heading message= {word + " at little lema Restobar"} />
    <button onClick={clickHandler}>click here</button>
  </div>)
};

# The props data is controlled outside of a component, and the state data is controlled by the component itself.
# The useState hook allows a component to have its own state.

# data transfer to sibling component
# Instead of prop drilling and lifting state up use React Context API
# Lifting State up
 Lifting state up is about cutting the state from the child component and moving it to the parent component's code, with the intent of making the state available in sibling components.Lifting up state can sometimes lead to prop drilling, which lowers maintainability and modularity of a React app.
 
# Prop drilling 
prop drilling is a situation where you are passing data from a parent to a child component, then to a grandchild component, and so on, until it reaches a more distant component further down the component tree, where this data is required.

function Main(props) { 
  return <Header msg={props.msg} />; 
};

function Header(props) { 
  return ( 
    <div style={{ border: "10px solid whitesmoke" }}> 
      <h1>Header here</h1> 
      <Wrapper msg={props.msg} /> 
    </div> 
  ); 
};

function Wrapper(props) { 
  return ( 
    <div style={{ border: "10px solid lightgray" }}> 
      <h2>Wrapper here</h2> 
      <Button msg={props.msg} /> 
    </div> 
  ); 
};

function Button(props) { 
  return ( 
    <div style={{ border: "20px solid orange" }}> 
      <h3>This is the Button component</h3> 
      <button onClick={() => alert(props.msg)}>Click me!</button> 
    </div> 
  ); 
};

function App() { 
  return ( 
    <Main  
      msg="I passed through the Header and the Wrapper and I reached the Button component"  
    /> 
  ); 
}; 

export default App;

# difference between passing Props and Context API
with the help of props teleporting is done through multiple level of components in parent child chain but with Context API it can be done directly to the destination

# Setting up Context API(An alternative way to working with state in React.)
Context Provider: Components that store the data
Consumer Provider:Components that use the data













