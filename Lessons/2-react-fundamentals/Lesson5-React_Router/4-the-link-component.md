### 4. The Link Component

<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/EZVVkrODWw8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=95" id="widget96" width="640" height="360" frameborder="0"></iframe>



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/jrW6zIa0Qdc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=97" id="widget98" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/1197d9d7bb255f2ff17eed63d295a80014c26814)



As you've seen, `Link` is a straightforward way to provide declarative, accessible navigation around your application. By passing a `to` property to the `Link` component, you tell your app which path to route to.

```js
<Link to="/about">About</Link>
```

If you're experienced with routing on the web, you'll know that  sometimes our links need to be a little more complex than just a string. For example, you can pass along query parameters or link to specific  parts of a page. What if you wanted to pass state to the new route? To  account for these scenarios, instead of passing a string to `Link`s `to` prop, you can pass it an object like this,

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

You won't need to use this feature all of the time, but it's good to know it exists. You can read more information about `Link` in the [official docs](https://reacttraining.com/react-router/web/api/Link).



### Quiz Question

When creating anchors for our app's routes, let's say we want 

```html
<a href="/members" class="members">Members</a>
```

in the DOM. How should we write this using React Router's `<Link>` component?

- [ ] ```html
  <Link to="members" class="members">Members</Link>
  ```

- [ ] ```html
  <a to="members" class="members">Members</a>
  ```

- [x] ```html
  <Link to="members" className="members">Members</Link>
  ```

- [ ] ```html
  <Link to="members" class="members" linkText="Members">
  ```

- 

## Link Recap

React Router provides a `Link` component which allows you  to add declarative, accessible navigation around your application.  You'll use it in place of anchor tags (`a`) as you're typically used to. React Router's `` component is a great way to make navigation through your app accessible for users. Passing a `to` prop to your link, for example, helps guide your users to an absolute path (e.g., `/about`):

```js
<Link to="/about">About</Link>
```

Since the `` component fully renders a proper anchor tag (``) with the appropriate `href`, you can expect it to behave how a normal link on the web behaves.

## Further Research

- [``](https://reacttraining.com/react-router/web/api/Link) at React Training
- [Source Code](https://github.com/ReactTraining/react-router/blob/master/packages/react-router-dom/modules/Link.js)