## 8. Better Practices

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/BnX0BPQPuY4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=87" id="widget88" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/constants/index.js)



### Question 1 of 2

![image-20200510103138218](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\4-react-and-redux\Lesson1-Managing_State\images\8-quiz-1)

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/oPC21DNJwyo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=89" id="widget90" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/blob/action-creators/index.js)

# Summary

In this section, we converted our actions to use JavaScript constants instead of strings. We also refactored our `.dispatch()` calls from passing in unique objects directly to them, to calling  special functions that create the action objects - these special  functions that create action objects are called **Action Creators**.