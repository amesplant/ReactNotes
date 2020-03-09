### 5. The Route Component

<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/ocZkC0MqGPY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=99" id="widget100" width="640" height="360" frameborder="0"></iframe>



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Ka19h7gvKi0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=101" id="widget102" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/66dcafce787f673b80622f808ca2dc4236aef0b0)



### Quiz Question



If the browser loads the URL `/houses/green`, which of the following Routes will match?

- [x] ```html
  <Route path="/houses" component={Houses} />
  ```

- [ ] ```html
  <Route exact path="/houses" component={Houes} />
  ```

- [x] ```html
  <Route path="/houses/green" component={Houses} />
  ```

- [ ] ```html
  <Route path="/" component={Houes} />
  ```




## Route Component Recap

The main takeaway from this section is that with a `Route` component if you want to be able to pass props to a specific component that the router is going to render, you'll need to use `Route`’s `render` prop. As you saw, `render` puts you in charge of rendering the component which in turn allows you  to pass any props to the rendered component as you'd like.

In summary, the `Route` component is a critical piece of  building an application with React Router because it's the component  which is going to decide which components are rendered based on the  current URL path.