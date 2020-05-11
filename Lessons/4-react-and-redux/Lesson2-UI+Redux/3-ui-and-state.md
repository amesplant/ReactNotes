## 3. UI + State

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/b9HpVHhDvL4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=101" id="widget102" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/707da3250f13adfef00fdbf032a563135cdf939a)



The changes we just added made it so whenever the Todo input field is  submitted, it will add a Todo item to the state...and whenever the Goal  input field is submitted, it will add a new Goal item to the state.

Let's break this down into the steps that happen. First, we need to  listen for when the buttons are clicked; we did this with the plain DOM `.addEventListener()` method:

```js
document.getElementById('todoBtn').addEventListener('click', addTodo)

document.getElementById('goalBtn').addEventListener('click', addGoal)
```

Pressing the `#todoBtn` will call `addTodo` which will add the new item to the state:

```js
function addTodo () {
  const input = document.getElementById('todo')
  const name = input.value
  input.value = ''

  store.dispatch(addTodoAction({
    name,
    complete: false,
    id: generateId()
  }));
}
```

This method will extract the information from the input field, reset the input field, and then dispatch an `addTodoAction` Action Creator with the text that the user typed into the input field.

So we're using the UI to change the state of our store, but these  changes are not reflecting the new state visually in the UI. Let's do  that, now.



> ## Need to Level Up Your DOM Skills?

> Both the content in the previous video, as well as the content in the following video depend on DOM-manipulation skills.

> - accessing elements with `document.getElementById()`
> - adding listeners with `.addEventListener()`
> - accessing the `.value` property on an element
> - creating a new element with `.createElement()`
> - adding new content with`.appendChild()`
> - etc.

> If you need to brush up on these skills, check out our course [JavaScript and the DOM](https://www.udacity.com/course/javascript-and-the-dom--ud117).



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/p3PtYdpqSO0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=103" id="widget104" width="640" height="360" frameborder="0"></iframe>



##### Before we proceed, there's one more feature to our UI that still needs  displaying. When a todo is completed, we want a line to appear through  it. Try thinking through the steps that would be needed. Each todo item  will need to listen for a click and change the text to strikethrough.  Now, try writing the code to actually make it work!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/pJ7wu1rU680?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=105" id="widget106" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/4219bd4cc8649f9fa1db65b57eb332150ec10c3f)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/aFYwjb2RSbE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=107" id="widget108" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/8b9fcbfa43d2fa8927e59fd2d0e61d6d0bb5737d)



# Summary

In this section, we connected our functioning state application with a front-end UI. We added some form fields and buttons to our UI that can  be used to add new Todo items and Goal items to the state. Updating the  state will *also* cause the entire application to re-render so  that the visual representation of the application matches that of the  info stored in the state object.

Now, we wrote all of this code ourselves. In the next section, we'll convert from using our custom library to using Redux.