## 4. Create Store: Getting and Listening

We'll start with a blank `index.js` file and create a factory function that creates store objects. Then we'll have the store keep track of the state, and we'll write the method to get the state from the store.

**index.js**
The state should have four parts

1. The state
2. Get the state
3. Listen to changes on the state
4. Update the state

#### 1. Set the state and 2. Get the state

````js
function createStore() {

    let state; // 1. set the state

    const getState = () => state;
    
    // 2. returns the state of the application
    return {
        getState
    }
}
````

#### 3. Listen to the changes on the state:

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

const store = createStoree();

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
            listener = listeners.filter((l) l = !== listener);
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

#### 4. Update the state

> Rule #1: Only an event can change the state of the store.

When an event takes place in a Redux application, we use a plain JavaScript object to keep track of what the specific event was. This object is called an **Action**.

````js
{
  type: "ADD_PRODUCT_TO_CART"
}
````

What makes this plain JavaScript object special in Redux, is that every Action must have a **type** property. The purpose of the type property is to let our app (Redux) know exactly what event just took place. 

Now, since an Action is just a regular object, we can include extra data about the event that took place:

````js
{
  type: "ADD_PRODUCT_TO_CART",
  productId: 17
}
````

Pass as little data as possible in each action. That is, prefer passing the index or ID of a product rather than the entire product object itself.

**Action Creators** are functions that _create/return_ action objects. For example:

````js
const addItem = item => ({
  type: ADD_ITEM,
  item
});
````

### Quiz Results

````js
// Valid Action Creator
const receivePost = post => ({
  type: RECEIVE_POST,
  post
});

// Valid Action Crator
const receivePost = post => ({
  type: RECEIVE_POST,
  post: post
}); 

// Valid Action
const clearErrors = {
  type: CLEAR_ERRORS
};

// Valid Action
const addSeven = {
  type: 'ADD_NUMBER',
  number: 7
};

// Not Valid Action -- missing type
const removeComments = {
  comments: null
};
````

Both **receivePost** functions are _action creators_, which extrapolate the creation of an action object to a function. 
**clearErrors** and **addSeven**, on the other hand, are _action objects_ with a valid **type** key and optional payload. 
**removeComments** does not include a type key and is an invalid action.