# 2. React as our UI



In this lesson, we're going to move away from our application being plain  HTML and convert it to being powered by React. To do that, we'll need to add a number of libraries:

- [react](https://www.npmjs.com/package/react)
- [react-dom](https://www.npmjs.com/package/react-dom)
- [babel](https://www.npmjs.com/package/babel)

Here are the packages that we'll be adding in the next video:

```html
<script src="https://unpkg.com/react@16.3.0-alpha.1/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@16.3.0-alpha.1/umd/react-dom.development.js"></script>
<script src="https://unpkg.com/babel-standalone@6.15.0/babel.min.js"></script>
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/UGxbnapRJnQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=127" id="widget128" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/97fcd0ad442fe9787c00dad9c8b53fd8e07b98a2)



The changes we've just implemented should look pretty familiar - they were  just converting parts of our app from HTML to being powered by React  Components. 

## Combining React and Redux

Alrighty, so you've learned React. You've built Redux and used it in a regular HTML application. But now we've started converting that HTML to a React application. In the following video we're going to start  connecting the React Components to the Redux store.

I want you to pay attention to a few things in the next screencast:

- where the `store.dispatch()` code goes in a React component
- how a React component is passed the Redux store as a prop



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/vxwzO_U0UC4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=129" id="widget130" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/6b61c0a6e557603c12a8ef8d6062e9d688df11eb)



In order to save time, we used an uncontrolled component for our input field.

## `ref`

> [Refs provide a way to access DOM nodes or React elements created in the render method.](https://reactjs.org/docs/refs-and-the-dom.html#callback-refs)

## When to Use Refs

The [docs](https://reactjs.org/docs/refs-and-the-dom.html#callback-refs) outline a few good use cases for `ref`s:

> - Managing focus, text selection, or media playback.
> - Triggering imperative animations.
> - Integrating with third-party DOM libraries.



Let's take a look at a similar example:

```js
class Color extends React.Component {
  alertTextInput = e => {
    e.preventDefault();
    alert(this.colorElement.value);
  };

  render() {
    return (
      <div>
        <input
          type="text"
          placeholder="Add Input"
          ref={(inputElement) => this.colorElement = inputElement}
        />

        <button onClick={this.alertTextInput}>Alert Input</button>
      </div>
    );
  }
}
```

In the line `ref={(inputElement) => this.colorElement = inputElement}`, `inputElement` is a reference to the `input` DOM element. We are storing a reference to the `input` DOM element in the `colorElement` instance property of the `Color` class.

Please note:

> [React will call the ref callback with the DOM element when the component mounts, and call it with `null` when it unmounts. Refs are guaranteed to be up-to-date before `componentDidMount` or `componentDidUpdate` fires.](https://reactjs.org/docs/refs-and-the-dom.html#callback-refs)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/0Z6YGs9hbMQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=131" id="widget132" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/494c9a91e01472ddc87935777e84d82e046010c9)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/G8pqzASO4ws?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=133" id="widget134" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/14bb2cd7b0c247e9429c075cff411b1cbb08a478)



#### `componentDidMount()`

> [`componentDidMount()`  is invoked immediately after a component is mounted (inserted into the  tree)...If you need to load data from a remote endpoint, this is a good  place to instantiate the network request.](https://reactjs.org/docs/react-component.html#componentdidmount)

#### `forceUpdate()`

> [By default, when your component’s state or props change, your component will re-render. If your `render()` method depends on some other data, you can tell React that the component needs re-rendering by calling `forceUpdate()`.](https://reactjs.org/docs/react-component.html#forceupdate)

> [Calling `forceUpdate()` will cause `render()` to be called on the component, skipping `shouldComponentUpdate()`. This will trigger the normal lifecycle methods for child components, including the `shouldComponentUpdate()` method of each child. React will still only update the DOM if the markup changes.](https://reactjs.org/docs/react-component.html#forceupdate)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/BtBRCH8PyRI?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=135" id="widget136" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/c7d050135ca6bf5ce73a79da51b198e5a90a0cfc)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/XCWV20iFvBU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=137" id="widget138" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/d3762be0264ef0395c332a75ba75558135967f1e)



# Summary

In this section, we converted our plain HTML application to one using React Components. We didn't implement any new features. Instead, we  just improved the code's organization by breaking out separate parts  into reusable chunks.