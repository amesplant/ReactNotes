# Lesson 2: Rendering UI with React

## 1. Rendering UI Intro

## 2. Creating Elements and JSX

> ### React's **.createElement()** 
> method takes **in** a *description of an element* 
> and **returns** a *plain JavaScript object*.

````
React.createElement( /* type */, /* props */, /* content */ );
````
> `type`    | either a string or a React Component
> `props`   | either null or an object
> `content` | null, a string, a React Element, or a React Component


> ### Virtual DOM
> A virtual DOM is not real DOM elements, but rather *objects that describe real DOM nodes*
> when we call react.createElement( ... ) we haven't actually created anything in the DOM yet
> it isn't until we say ##render## that we've actually created a ##real## DOM element

### Intro to Components
[Components and Props](https://reactjs.org/docs/components-and-props.html)
 
 Components refer to reusable pieces of code ultimately responsible for returning HTML to be rendered onto the page.
 ````js
 import React, { Component } from 'react'; // our component class will need to extend from the base class React.Component
 
 class ContactList extends Componenent {
     render () {
          const people = [
              { name: 'Ames' },
              { name: 'MJ' }
          ]
          
          // element to be rendered
          return <ol> 
              {poeple.map((person) => {
                  <li key={person.name}>{person.name}</li> // key={person.name} required property for JSX
              })}
          </ol>
     }
 }
 
 ReactDOM.render(
     <ContactList />,
     document.getElementById('root')
 )
````

## Passing properties (props) into our Component
We can now add properties (props) into our ContactList, which is the benefit of using components (reusability)
````js
// This is the stock create-react-app application

//import React from 'react';
import React, { Component } from 'react'; // our component class will need to extend from the base class React.Component

// import logo from './logo.svg'; // remove from stock create-react-app
// import './App.css'; // remove from stock create-react-app

// add in ContactList component
//class ContactList extends React.Component {
class ContactList extends Component { // since we imported { Component } with react, we can simplify React.Component to just Component
  render() {
    /*const people = [
      { name: 'Amy'},
      { name: 'MJ'}
    ]*/

    const people = this.props.contacts; // when calling ContactList, a property named contact will be passed in
    
    return <ol>
      {people.map((person) => (
        <li key={person.name}>{person.name}</li> // key={person.name} required property for JSX
      ))}
    </ol>
  }
}

class App extends Component {
  render() {
    return (
      <div className="App">
        <ContactList contacts={[
          { name: 'Amy'},
          { name: 'Cat'}
        ]}/> 
        <ContactList contacts={[
          { name: 'MJ'},
          { name: 'Sam'},
          { name: 'Charlie' },
          { name: 'Martha' }
        ]}/> 
      </div>
    );
  }
}

export default App;

````

### Lesson Challenge

Answer the following questions and share your answers with your Study Group.

> 1) What is a component? How do components relate to props?

> 2) How do we know whether something should be a component in React?
