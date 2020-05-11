# 2. External Data



We're going to use a database to interact with our Todos application. We're  simulating the database to keep that aspect of the project less complex. This is the HTML script tag you need to add the database to your  application which we'll use in the following video:

```html
<script src="https://tylermcginnis.com/goals-todos-api/index.js"></script>
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/diArZ09Mw1U?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=151" id="widget152" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/ac11f181a90e77a21478e59c258d720a658ec869)

![image-20200510105634281](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson5-Asynchronous_Redux\images\2-quiz-1-2)

## 🔨Task

Add the following behavior to the project:

- When the app loads, `console.log` all of the todos and all of the goals that reside in our fake database.

#### Solution Code

Once you've tried your hand at tackling the task above, hover your mouse here for a possible solution. 



## Promise-Based API

The methods in the provided API are all Promise-based. Let's take a look at the `.fetchTodos()` method:

```js
API.fetchTodos = function () {
  return new Promise((res, rej) => {
    setTimeout(function () {
      res(todos);
    }, 2000);
  });
};
```

See how we're creating and returning a new `Promise()` object?

In the task above, you could've just fetched all of our todos and  then all of our Goals, but that's serial and is just making the user  wait an unnecessarily long amount of time. Since the API is  Promise-based, we can use `Promise.all()` to wait until all Promises have resolved before displaying the content to the user.

Promises are asynchronous, and this lesson is all about working with  asynchronous data and asynchronous requests. If you're feeling a little  unsure about Promises, check out [the Promise documentation on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) or check out our [JavaScript Promises course](https://www.udacity.com/course/javascript-promises--ud898).



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/94ipRgIS9CY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=153" id="widget154" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/98d9b5468262eb4ea786cb55c3d68ed9de78af09)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/KS0xPETRzRA?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=155" id="widget156" width="640" height="360" frameborder="0"></iframe>



## Implementing a Loading Indicator

At this point, when we refresh our app, only the UI seems to load. There  is a noticeable delay before any of the data (i.e., todos and goals)  actually appears on the screen. To ensure a smooth experience for users, it would be great if we can have a loading indicator on the screen as  content is being fetched.

How would you implement this feature? Should this be tracked in the  state? Do we need to make a new component? What about our reducers --  should they require any new logic? Please write your thoughts below.

------

### Your reflection

**We need to create a reducer to track the state of loading.**

### Things to think about

Thanks for your response.



💫Remember that the `render()`  has to be a pure function and it runs before `componentDidMount()`.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/w5fQmGBKn1g?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=157" id="widget158" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/6bb7f0d521986a316b9aa45cac4f2fae886c4bfc)



# Summary

In this section, we looked at how to work with an external API. We added a new action (`RECEIVE_DATA`), created a new action creator, and built a new reducer...all to handle  the different states our app can be in while getting our remote data:

- before the app has the data
- while the app is fetching the data
- after the data has been received

In the next section, we'll look at how to optimistically update the UI based on the API actions that are performed.