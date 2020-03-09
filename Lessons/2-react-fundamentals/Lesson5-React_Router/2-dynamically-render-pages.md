### 2. Dynamically Render Pages

As the app currently functions, there's no way to add new contacts! That's a shame because I really need to add Richard to my list of contacts. So let's create a form that'll let us create new contacts and save them to the server.



> ### Quiz Question
>
> We're about to create a form that will create new contacts. Where should the code for the form UI go?
>
> - [ ] in `App.js`
> - [ ] in `ListContacts.js`
> - [ ] in `index.js`
> - [x] in a new component

- 

We don't want the form to display all of the time, so we'll start out by  having the form show up only if a setting is enabled. We'll store this  setting in `this.state`. Doing it this way will give us an idea of how React Router functions.



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/I4wTc_ulrME?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=85" id="widget86" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/e4a527dbd7a5e1d3fca2a92251556024d834258a)



We packed quite a bit of important changes in this little video! We  created the CreateContact component that'll be in charge of the form to  create new contacts. In staying with the general React theme of favoring composition, we created this as a standalone component and used  composition by adding it to the `render()` method in the `App` component.

In an attempt to do an *extremely* simple recreation of how React Router works, we added a `screen` property to `this.state`, and used this property to control what content should display on the screen. If `this.state.screen` is `list` then we'll show the list of all existing contacts. If `this.state.screen` is `create` then we'll show the CreateContact component.



## Short-circuit Evaluation Syntax

In this video and when we created the Now showing section from earlier, we used a somewhat odd looking syntax:

```js
{this.state.screen === 'list' && (
  <ListContacts
  contacts={this.state.contacts}
  onDeleteContact={this.removeContact}
  />
)};
```

and

```js
{this.state.screen === 'create' && (
  <CreateContact />
)}
```

This can be a little confusing with both the JSX code for a component and the code to run an expression. But this is really just the logical  expression `&&`:

```js
expression && expression
```

What we're using here is a JavaScript technique called **short-circuit evaluation**. If the first expression evaluates to `true`, then the second expression is run. However, if the first expression evaluates to `false`, then the second expression is skipped. We're using this as a guard to first verify the value of `this.state.screen` before displaying the correct component.

For a deeper dive into this, check out [the short-circuit evaluation info on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators#Short-circuit_evaluation).



## Add A Button

Right now we have to manually change the state to get the app to  display the different screens. We want the user to be able to control  that in the app itself, so let's add a button!



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/AX-ZpaliAYc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=87" id="widget88" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/93ff543181f0558ee5be9aab8eef771c47269451)



## Dynamic Routing Recap

In the code we added in this section, we tried our attempt at using  state to control what content displays to the user. We saw things break  down, though, when we used the back button. 

Now, let's switch over to using React Router to manage our app's screens.