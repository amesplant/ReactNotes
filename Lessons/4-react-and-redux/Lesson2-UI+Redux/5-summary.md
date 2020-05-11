## 5. Summary

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/45ileyqFeGw?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=113" id="widget114" width="640" height="360" frameborder="0"></iframe>

#### Lesson Challenge #1

Read these articles: [The what and why of Redux](https://blog.pusher.com/the-what-and-why-of-redux/) and [Leveling Up with React: Redux](https://css-tricks.com/learning-react-redux/). Answer the following questions (in your own words) and share your answers with your classmates:

1) What are the advantages of using Redux?

2) Describe the 3 principles Redux follows.

#### Lesson Challenge #2

Take a look at the Workspace below and fix the 8 bugs in the `index.html` file.

```html
<!DOCTYPE html>
<html>

  <head>
    <title>Udacity Todos Goals</title>
    <script src='https://cdnjs.cloudflare.com/ajax/libs/redux/3.7.2/redux.min.js'></script>
  </head>

  <body>
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
    <script type='text/javascript'>
      function generateId() {
        return Math.random().toString(36).substring(2) + (new Date()).getTime().toString(36);
      }

      // App Code
      const ADD_TODO = 'ADD_TODO'
      const REMOVE_TODO = 'REMOVE_TODO'
      const TOGGLE_TODO = 'TOGGLE_TODO'
      const ADD_GOAL = 'ADD_GOAL'
      const REMOVE_GOAL = 'REMOVE_GOAL'

      function addTodoAction(todo) {
        return {
          todo,
        }
      }

      function removeTodoAction(id) {
        return {
          id,
        }
      }

      function toggleTodoAction(id) {
        return {
          id,
        }
      }

      function addGoalAction(goal) {
        return {
          goal,
        }
      }

      function removeGoalAction(id) {
        return {
          id,
        }
      }

      function todos(state, action) {
        switch (action.type) {
        case ADD_TODO:
          return state.push([action.todo])
        case REMOVE_TODO:
          return state.filter((todo) => todo.id !== action.id)
        case TOGGLE_TODO:
          return state.map((todo) => todo.id !== action.id ? todo :
            Object.assign({}, todo, {
              complete: !todo.complete
            }))
        default:
          return state
        }
      }

      function goals(state = {}, action) {
        switch (action.type) {
        case ADD_GOAL:
          return state.concat([action.goal])
        case REMOVE_GOAL:
          return state.filter((goal) => goal.id !== action.id)
        default:
          return state
        }
      }

      const store = Redux.createStore(Redux.combineReducers({
        todos,
        goals,
      }))

      store.subscribe(() => {
        const {
          goals,
          todos
        } = store.getState()

        document.getElementById('goals').innerHTML = ''
        document.getElementById('todos').innerHTML = ''

        goals.forEach(addGoalToDOM)
        todos.forEach(addTodoToDOM)
      })

      // DOM code
      function addTodo() {
        const input = document.getElementById('todo')
        const name = input.value
        input.value = ''

        store.dispatch(addTodoAction({
          name,
          complete: false,
          id: generateId()
        }))
      }

      function addGoal() {
        const input = document.getElementById('goal')
        const name = input.value
        input.value = ''

        store.dispatch(addGoalAction({
          id: generateId(),
          name,
        }))
      }

      document.getElementById('todoBtn')
        .addEventListener('click', addTodo)

      document.getElementById('goalBtn')
        .addEventListener('click', addGoal)

      function createRemoveButton(onClick) {
        const removeBtn = document.createElement('button')
        removeBtn.innerHTML = 'X'
        removeBtn.addEventListener('click', onClick)
        return removeBtn
      }

      function addTodoToDOM(todo) {
        const node = document.createElement('li')
        const text = document.createTextNode(todo.name)

        const removeBtn = createRemoveButton(() => {
          store.dispatch(removeTodoAction(todo.id))
        })

        node.appendChild(text)
        node.appendChild(removeBtn)
        node.style.textDecoration = todo.complete ? 'line-through' : 'none'
        node.addEventListener('click', () => {
          store.dispatch(toggleTodoAction(todo.id))
        })

        document.getElementById('todos')
          .appendChild(node)
      }

      function addGoalToDOM(goal) {
        const node = document.createElement('li')
        const text = document.createTextNode(goal.name)
        const removeBtn = createRemoveButton(() => {
          store.dispatch(removeGoalAction(goal.id))
        })

        node.appendChild(text)
        node.appendChild(removeBtn)

        document.getElementById('goals')
          .append(node)
      }
    </script>
  </body>

</html>
```

