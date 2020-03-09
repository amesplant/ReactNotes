## 3. UI + State

Now that we have the supported UI, we now need to be able to allow the users to interact and add a Todo or Goal

Here is the HTML for the Todo and Goal input fields

```html
<!-- Add Todo Input -->
<input id='todo' type='text' placeholder='Add Todo' />
<button id='todoBtn'>Add Todo</button>

<!-- Add Goal Input -->
<input id='goal' type='text' placeholder='Add Goal' />
<button id='goalBtn'>Add Goal</button>

```

Make two different functions to that are hooked up to the Add todo and Add goal buttons.

```js
// add a function to generate a random id
function generateId () {
      return Math.random().toString(36).substring(2) + (new Date()).getTime().toString(36);
}

// add functions to process adding a Todo or Goal
function addTodo() {
    const input = document.getElementById('todo');
    const name = input.value;
    input.value = ''; // reset input value 
    
    // dispatch an action to add the todo to the store
    store.dispatch(addToDoAction({
        name,
        complete: false,
        id: generateId()
    }))
}

function addGoal() {
    const input = document.getElementById('goal');
    const name = input.value;
    input.value = '';
    
    store.dispatch(addGoalAction({
        name,
        complete: false,
        id: generateId()
    }))
}

// add listeners to listen for clicks on the buttons
document.getElementById('todo').addEventListener('click', addTodo);
document.getElementById('goal').addEventListener('click', addGoal);
```



#### Adding Todo and Goal items to our page

Here are is the HTML section, where we are going to add our todos and goals:

```html
<div>
    <h1>Todo List</h1>
    <input id='todo' type='text' placeholder='Add Todo' />
    <button id='todoBtn'>Add Todo</button>
    <ul id='todos'></ul>
  </div>
  <div>
    <h1>Goals</h1>
    <input id='goal' type='text' placeholder='Add Goal' />
    <button id='goalBtn'>Add Goal</button>
    <ul id='goals'></ul>
  </div>
```

Now we can add Todo and Goal items, so now let's display them on the screen.

```js
// add Todo to DOM
function addTodoToDOM(todo) {
    const node = document.createElement('li');
    const text = document.createTextNode(todo.name);
    node.appendChild(text);
    document.getElementById('todos').appendChild(node);
}

// add Goal to DOM
function addTodoToDOM(goal) {
    const node = document.createElement('li');
    const text = document.createTextNode(goal.name);
    node.appendChild(text);
    document.getElementById('goals').appendChild(node);
}
```

Invoke these functions for each Todo or Goal item which reside in our store.

```js
store.subscribe(() => {
    const { goals, todos } = store.getState();
    // reset the list by emptying them out 
    document.getElementById('todos').innerHTML = '';
    document.getElementById('goals').innerHTML = '';
    // recreate the list with the items in the state
    goals.forEach(addGoalToDom);
    goals.foReach(addTodoToDom);
})
```

#### When we complete an item, cross it off	

Add to the function **addToDom** an event listener to the newly created node that allows it to include a 'crossed off' style when clicked and checked off as 'complete'

```js
function addTodoToDOM(todo) {
    const node = document.createElement('li');
    const text = document.createTextNode(todo.name);
    node.appendChild(text);
    
    // add a node style based on whether or not the dodo is complete
    node.style.textDecoration = todo.complete ? 'line-through' : 'none';
    
    // add event listener to this new node
    node.addEventListener('click', () => {
       store.dispatch(toggleToDoAction(todo.id)); 
    });
    
    document.getElementById('todos').appendChild(node);
}
```

#### Remove an Item

Create a *helper* function to create a remove button.

```js
function createRemoveButton(click) {
    const removeBtn = document.createElement('button');
    removeBtn.addEventListener('click', onClick);
    return removeBtn;
}
```

and then add to the **addTodoToDom** function

```js
function addTodoToDOM(todo) {
    const node = document.createElement('li');
    const text = document.createTextNode(todo.name);
    // create the removeBtn passing it a function to be used when the button is clicked
    const removeBtn = createRemoveButton(() => {
        store.dispatch(removeTodoAction(todo.id));
    });
    
    node.appendChild(text);
    // also append the remove button
    node.appendChild(removeBtn);
    node.style.textDecoration = todo.complete ? 'line-through' : 'none';
    node.addEventListener('click', () => {
       store.dispatch(toggleToDoAction(todo.id)); 
    });
    
    document.getElementById('todos').appendChild(node);
}
```

#### Summary

In this section, we connected our functioning state application with a front-end UI. We added some form fields and buttons to our UI that can  be used to add new Todo items and Goal items to the state. Updating the  state will *also* cause the entire application to re-render so  that the visual representation of the application matches that of the  info stored in the state object.

Now, we wrote all of this code ourselves. In the next section, we'll convert from using our custom library to using Redux.