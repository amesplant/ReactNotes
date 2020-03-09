### 3. The BrowserRouter Component

As we've just seen, when the user presses the 'back' button in the  browser, they will probably have to refresh the page to see the proper  content at that location. This isn't the best experience for our user!  When we update location, we can update the app as well using JavaScript. This is where React Router comes in. 

## Install React Router

To use React Router in our app, we need to install [react-router-dom](https://www.npmjs.com/package/react-router-dom).

```bash
npm install --save react-router-dom
```

Let's see it in action!



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/qvy-_Pu9QNU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=89" id="widget90" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/fbd0cea0839d018209a19d468fc1661da9f9033a)



## BrowserRouter

The first component we'll look at is BrowserRouter.



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/bhjvF7Qt7K0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=91" id="widget92" width="640" height="360" frameborder="0"></iframe>



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/uIYOoQKwKfU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=93" id="widget94" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/d1b067febbfc467563742fc3b52b6a34486ebde5)



What's nice about React Router is that everything is just a component. This  makes using it nice, but it also makes diving into the code more  convenient as well. Let's take a look at what exactly BrowserRouter is  doing under the hood.

Here is the code straight from the React Router repository.

```js
class BrowserRouter extends React.Component {
  static propTypes = {
    basename: PropTypes.string,
    forceRefresh: PropTypes.bool,
    getUserConfirmation: PropTypes.func,
    keyLength: PropTypes.number,
    children: PropTypes.node
  }

  history = createHistory(this.props)

  render() {
    return <Router history={this.history} children={this.props.children} />
  }
}
```

When you use `BrowserRouter`, what you're really doing is rendering a `Router` component and passing it a `history` prop. Wait, what is `history`? `history` comes from the [history](https://github.com/ReactTraining/history) library (also built by React Training). The whole purpose of this  library is it abstracts away the differences in various environments and provides a minimal API that lets you manage the history stack,  navigate, confirm navigation, and persist state between sessions.

So in a nutshell, when you use `BrowserRouter`, you're creating a `history` object which will listen to changes in the URL and make sure your app is made aware of those changes.



##### Let's make sure you've performed the necessary steps. Check off each of the following:

Task List

- 

## `BrowserRouter` Component Recap

In summary, for React Router to work properly, you need to wrap your whole app in a `BrowserRouter` component. Also, `BrowserRouter` wraps the history library which makes it possible for your app to be made aware of changes in the URL. 

### Further Research

- [history](https://github.com/reacttraining/history)