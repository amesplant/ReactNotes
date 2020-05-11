## 2. UI

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/8IkNVrCqtvo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=97" id="widget98" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/3cb66af8ea36d4be3e80037ad76cef0ed58d24c8)



# What We're Going to Build

Now that we have an `index.html` file and all of the  JavaScript code has been transferred over to script tags, let's start  adding in a User Interface. Since our project has two pieces of state,  we'll need two areas:

1. Todo list area
2. Goals area 



[![Screenshot of the Todo List app.](https://video.udacity-data.com/topher/2018/March/5abbeeea_nd019-redux-l2-basic-ui/nd019-redux-l2-basic-ui.jpg)This  is what our UI should look like when we're finished: a Todo List area  with an input to add a new Todo item, and a Goals area with an input to  add a new Goal. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/9f490b7a-d61c-4b1e-b399-3451d6525ec1/concepts/11c90108-847f-4763-8c0a-3bd2009246ae#)



So this is what we're going for. It's not the best looking website ever  created, but this isn't a course on CSS ;-). If you want to make it  stunningly beautiful, feel free to add some CSS to your project 👍🏼

We already have the Redux portion of our application working, but so  far, we've just been manually running snippets of code to interact with  the Redux Store. Let's create the UI above so that we can interact with  the store using the browser.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/0M2gm4-IbGs?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=99" id="widget100" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/c800637efb41fee3f4ea2a9392eb7a3025aac69f)



# Summary

In this section, we added some minimal UI to our application. The actually state of our app hasn't changed at all, though.

In the next section, we'll hook up our shiny new UI to our state so  that entering content via the UI will update the application's state.