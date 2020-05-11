# 13. Using React Router



We're pretty much finished with everything in our app! Our final step is to  get the app to handling routing. We'll do this we React Router.

```bash
yarn add react-router-dom
```



### Quick [React Router](https://reacttraining.com/react-router/web/guides/philosophy) Review

### `BrowserRouter` Component

`BrowserRouter` listens for changes in the URL and makes sure that the correct screen shows up when the URL changes.

Doing this: 

```js
<BrowserRouter>
   <App />
</BrowserRouter>
```

will allow us to 

- use the other components `browser-router-dom` comes with inside of our app
- listen to the URL so that whenever the url changes, the routing components will be notified of the change

### `Link` Component

```js
<Link to="/about">About</Link>
```

Users navigate through React apps with the help of the `Link` Component. 

The `Link` component talks to the `BrowserRouter` and tells it to update the URL. By passing a `to` property to the `Link` component, you tell your app which path to route to.

What if you wanted to pass state to the new route? Instead of passing a string to `Link`s `to` prop, you can pass it an object like this:

```js
<Link to={{
 pathname: '/courses',
 search: '?sort=name',
 hash: '#the-hash',
 state: { fromDashboard: true }
}}>
 Courses
</Link>
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/_cB8CE_Q3Yk?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=269" id="widget270" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-chirper-app/commit/512ddca69dd99d67acf4b9795b1000c2e728e899)