# 5. Leveraging Thunks in our App



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/WysYSogVCAo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=169" id="widget170" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/f791da39440d43bcd3f24ed37fa078ecaf72cb97)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/GAn1-rLDmYc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=171" id="widget172" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/6fb6208f7f67dfe601a8efa9de44a10208863be9)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Bzn33iPkKDA?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=173" id="widget174" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/e40512f5cd22b35c6461fa334636aaa1eb9f27d2)



## More Asynchronous Options

The most common requests I get for this course are around more  advanced data-fetching topics with Redux. I've resisted because  typically they bring in *a lot* of complexity, while the benefits aren't seen until your data-fetching needs become large enough. With  that said, now that you have a solid foundation on Redux and  specifically, asynchronous Redux, you'll be in a good position to read  up on the different options to decide if any would work best for the  type of application you're working on. I encourage to read up on both of the other (popular) options.

- [Redux Promise](https://github.com/redux-utilities/redux-promise) - FSA-compliant promise middleware for Redux.
- [Redux Saga](https://github.com/redux-saga/redux-saga) - An alternative side effect model for Redux apps



# Summary

In this section, we used the thunk library that we installed in the  previous section to make our code more singularly-focused and  maintainable. We converted the:

- Goals code to use thunks
- Todos code to use 
- initial data fetching to use thunks 