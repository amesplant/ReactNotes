[Home](https://github.com/amesplant/ReactNotes#react-notes) / [Lessons](https://github.com/amesplant/ReactNotes/tree/master/Lessons) / Redux

# Lesson 1: Managing State

## The Store
We combine the three items below and the state tree object itself into one unit which we call the **store**. 

- [ ] getting the state
- [ ] listening for changes to the state
- [ ] updating the state

## Create Store: Getting and Listening

We'll start with a blank `index.js` file and create a factory function that creates store objects. Then we'll have the store keep track of the state, and we'll write the method to get the state from the store.

**index.js
The state should have four parts
1. The state
2. Get the state
3. Listen to changes on the state
4. Update the state

### 1. Set the state and 2. Get the state

````js
function createStore() {

    let state; // 1. set the tate

    const getState = () => state 
    
    // 2. returns the state of the application
    return {
        getState
    }
}
````

### 3. Listen to the changes on the state:

It would be nice if we provide to the user a subscribe method, they then could pass subscribe a callback function ... and whenever the state changes internally, we can invoke the callback function ....

````js
function createStore() {

    let state; // 1. set the tate

    const getState = () => state 
    
    // 2. returns the state of the application
    return {
        getState
    }
}

const store = createState();

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
})

// they might want to subscribe more than one time ...
store.subscribe(() => {
    console.log("The store changed: ", store.getState());
})

````

Internally, we need to keep track every time the user calls subscribe.
And then eventually, when we add the functionality to be able to change the state of our store, we need to call every function that was passed in when subscribe was invoked....

````js
function createStore() {

    let state; 
    let listeners = []; // create a new array

    const getState = () => state 

    // create our subscribe method .. they could then pass subscribe a callback function
    // and when the state changes internally .. we invoke the callback function
    const subscribe = (listener) => { 
        listeners.push(listener);
    }
    
    return {
        getState,
        subscribe // return subscribe
    }
}

const store = createState();

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
})

store.subscribe(() => {
    console.log("The store changed: ", store.getState());
})

````
### unsubscribe

````js
function createStore() {

    let state; 
    let listeners = []; 

    const getState = () => state 

    const subscribe = (listener) => { 
        listeners.push(listener);
        return () => {
            listener = listeners.filter((l) = l !== listener);
        }
    }
    
    return {
        getState,
        subscribe // return subscribe
    }
}

const store = createState();

store.subscribe(() => {
    console.log("The new state is: ", store.getState());
})

const unsubscribe = store.subscribe(() => {
    console.log("The store changed: ", store.getState());
})

// now invoke to remove that specific listener
unsubscribe();

````

### 4. Updating State
| Only an event can change the state of the store.
