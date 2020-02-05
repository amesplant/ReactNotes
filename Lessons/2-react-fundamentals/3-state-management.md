### 2 | React Fundamentals
# Lesson 3: State Management

## 2.Pass Data Into Components With Props
> Props | allow you to pass data into your components
>
> Functional Components 
>
> Controlled Components | allow you to hook up the forms in your application to your component state

> We can think of passing in props to components just as we pass arguments into functions. 
> Just as we can access arguments passed into a regular JavaScript function, we can access a 
> component's props with this.props (or props in stateless functional components).


### We will be building a Contacts App
- display contacts and detail
- filter contacts
- refresh the list of contacts
- remove contacts
- add contacts

### App.js
modify our previous App.js for our **Contacts App**
````js
import React, { Component } from 'react'; // our component class will need to extend from the base class React.Component
import ListContacts from './ListContacts';

const contacts = [
  {
    "id": "karen",
    "name": "Karen Isgrigg",
    "handle": "karen_isgrigg",
    "avatarURL": "http://localhost:5001/karen.jpg"
  },
  {
    "id": "richard",
    "name": "Richard Kalehoff",
    "handle": "richardkalehoff",
    "avatarURL": "http://localhost:5001/richard.jpg"
  },
  {
    "id": "tyler",
    "name": "Tyler McGinnis",
    "handle": "tylermcginnis",
    "avatarURL": "http://localhost:5001/tyler.jpg"
  }
 ];


class App extends Component {
  render() {
    return (
      <div className="App">
        <ListContacts  contacts={contacts} /> 
      </div>
    );
  }
}

export default App;
````

### ListContacts.js
This file is reponsible for listing all of the contacts.
First we will build the ListContacts and console.log the properties to make sure they are getting passed down from App.js
````js
import React, { Component } from 'react';

class ListContacts extends Component {
    // describe how this component should look
    render() { // render method describes the UI of our component
        console.log('Props: ', this.props)
        return (
            <ol className='contact-list'>
                
            </ol>
        )
    }
}
export default ListContacts
````

Next, we will map over our List of Contacts to display them, since currently we are only console logging them.

### New Ordered List
````js
<ol className='contact-list'>
    {this.props.contacts.map((contact) => (
        // using ()) instead of {}} for the implicit return of ES6 arrow function
        <li key={contact.id}>
            {contact.name}
        </li>
    ))}
</ol>
````

## Passing mutliple pieces of information
- Name
- Twitter Handle
- Avatar

### Our new List Item
````js
<li key={contact.id} className='contact-list-item'>
    <div
        className='contact-avatar'
        style={{ // first { denotes using JS, second { denotes passing in an object
            backgroundImage: `url(${contact.avatarURL})` // ` to denote ES6 template string ${variable}
        }}
    ></div>
    <div className='contact-details'>
        <p>{contact.name}</p>
        <p>{contact.handle}</p>
    </div>
    <button className='contact-remove'>
        Remove
    </button>
</li>
````

### 6. Functional Components
If all your comopnent has is a **render** method, use a regular function to create the component.

**Class Component**
````js
class User extends React.component {
  render() {
    return (
      <p>Username: {this.props.username}</p>
     )
  }  
 }
````
**Stateless Functional Component**
````js
function User(props) {
  return (
    <p>Username: {props.username}</p>
   )
}
````

#### Exercises
Change these as needed:

**App.js**
````js
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';
import MovieCardsList from './MovieCardsList';

const profiles = [
  {
    id: 1,
    userID: '1',
    favoriteMovieID: '1',
  },
  {
    id: 2,
    userID: '2',
    favoriteMovieID: '1',
  },
  {
    id: 3,
    userID: '4',
    favoriteMovieID: '5',
  },
  {
    id: 4,
    userID: '5',
    favoriteMovieID: '2',
  },
  {
    id: 5,
    userID: '3',
    favoriteMovieID: '5',
  },
  {
    id: 6,
    userID: '6',
    favoriteMovieID: '4',
  },
];

const users = {
  1: {
    id: 1,
    name: 'Jane Jones',
    userName: 'coder',
  },
  2: {
    id: 2,
    name: 'Matthew Page',
    userName: 'mpage',
  },
  3: {
    id: 3,
    name: 'Autumn Green',
    userName: 'user123',
  },
  4: {
    id: 3,
    name: 'John Doe',
    userName: 'user123',
  },
  5: {
    id: 5,
    name: 'Lauren Johnson',
    userName: 'user123',
  },
  6: {
    id: 6,
    name: 'Nicholas Lain',
    userName: 'user123',
  },
};

const movies = {
  1: {
    id: 1,
    name: 'Planet Earth 1',
  },
  2: {
    id: 2,
    name: 'Selma',
  },
  3: {
    id: 3,
    name: 'Million Dollar Baby',
  },
  4: {
    id: 4,
    name: 'Forrest Gump',
  },
  5: {
    id: 5,
    name: 'Get Out',
  },
};

class App extends Component {
  render() {
    return (
      <div>
        <header className="App-header">
          <img src={logo} className="App-logo" alt="logo" />
          <h1 className="App-title">ReactND - Coding Practice</h1>
        </header>
        <h1>How Popular is Your Favorite Movie?</h1>
        <MovieCardsList profiles={profiles} movies={movies} users={users} />
      </div>
    );
  }
}

export default App;
````

**App.js (as a Stateless Functional Component**

Since this component doesn't need to hold state, we can make it a Stateless Functional Component.
````js
const App = () => {
  return (
    <div>
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h1 className="App-title">ReactND - Coding Practice</h1>
      </header>
      <h1>How Popular is Your Favorite Movie?</h1>
      <MovieCardsList profiles={profiles} movies={movies} users={users} />
    </div>
  );
};

````

**MovieCard.js**
````js
import React from 'react';

const MovieCard = () => {

  const { users, usersWhoLikedMovie, movieInfo } = props;

  return (
    <li key={movieInfo.id}>
      <h2>{movieInfo.name}</h2>
      <h3>Liked By:</h3>

      {!usersWhoLikedMovie || usersWhoLikedMovie.length === 0 ? (
        <p>None of the current users liked this movie.</p>
      ) : (
        <ul>
          {usersWhoLikedMovie &&
          usersWhoLikedMovie.map(userId => {
            return (
              <li key={userId}>
                <p>{users[userId].name}</p>
              </li>
            );
            })}
        </ul>
      )}
    </li>
   );
}

export default MovieCard;
````

**MovieCard.js (as a Stateless Functional Component)**

Since this component doesn't need to hold state, we can make it a Stateless Functional Component.
````js
const MovieCard = props => {

  const { users, usersWhoLikedMovie, movieInfo } = props; // destructuring via ES6

  return (
    <li key={movieInfo.id}>
      <h2>{movieInfo.name}</h2>
      <h3>Liked By:</h3>

      {!usersWhoLikedMovie || usersWhoLikedMovie.length === 0 ? (
        <p>None of the current users liked this movie.</p>
      ) : (
        <ul>
          {usersWhoLikedMovie &&
            usersWhoLikedMovie.map(userId => {
              return (
                <li key={userId}>
                  <p>{users[userId].name}</p>
                </li>
              );
            })}
        </ul>
      )}
    </li>
  );
};
````

**MovieCardList.js**
````js
import React, { Component } from 'react';
import MovieCard from './MovieCard';

class MovieCardsList extends Component {
  render() {
    const { profiles, users, movies } = this.props; // destructuring via ES6
    const usersByMovie = {};

    profiles.forEach(profile => {
      const movieID = profile.favoriteMovieID;

      if (usersByMovie[movieID]) {
        usersByMovie[movieID].push(profile.userID);
      } else {
        usersByMovie[movieID] = [profile.userID];
      }
    });

    const movieCards = Object.keys(movies).map(id => (
      <MovieCard
        key={id}
        users={users}
        usersWhoLikedMovie={usersByMovie[id]}
        movieInfo={movies[id]}
      />
    ));

    //Return JSX
    return <ul>{movieCards}</ul>;
  }
}

export default MovieCardsList;
````

**MovieCardsList.js (as a Statesless Functional Component)**

Since this component just needs to render some data and does not need to keep track of the component's internal state, we can make it a Stateless Functional Component.
````js
const MovieCardsList = props => {

  const { profiles, users, movies } = props;
  const usersByMovie = {};

  profiles.forEach(profile => {
    const movieID = profile.favoriteMovieID;

    if (usersByMovie[movieID]) {
      usersByMovie[movieID].push(profile.userID);
    } else {
      usersByMovie[movieID] = [profile.userID];
    }
  });

  const movieCards = Object.keys(movies).map(id => (
    <MovieCard
    	key={id}
        users={users}
        usersWhoLikedMovie={usersByMovie[id]}
        movieInfo={movies[id]}
    />
	));

  // Return JSX
  return <ul>{movieCards}</ul>;
}
````

### Recap: Statless Functional Comonents
If your component does not keep track of internal state (i.e., all it really has is just a render() method), you can declare the component as a Stateless Functional Component.

Remember that at the end of the day, React components are really just JavaScript functions that return HTML for rendering. As such, the following two examples of a simple Email component are equivalent: 
````js
class Email extends React.Component {
 render() {
   return (
     <div>
       {this.props.text}
     </div>
   );
 }
}
````
````js
const Email = (props) => (
 <div>
   {props.text}
 </div>
);
````
In the latter example (written as an ES6 function with an implicit return), rather than accessing `props` from `this.props`, we can pass in `props` directly as an argument to the function itself. In turn, this regular JavaScript function can serve as the Email component's `render()` method.