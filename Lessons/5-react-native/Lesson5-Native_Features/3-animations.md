# 3. Animations



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/lyM8LcmrdS8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=427" id="widget428" width="640" height="360" frameborder="0"></iframe>



Animations are a fundamental aspect of any native application. Because of this,  React Native comes built in with an animations library called `Animated`. The whole idea of Animated is that it "focuses on declarative  relationships between inputs and outputs, with configurable transforms  in between, and simple start/stop methods to control time-based  animation execution." In other words, Animated allows you to establish  different types of transformations on specific values. For example, you  could easily animate an image's `opacity` property from 0 to 1, giving the effect that the image is slowly appearing. 

There are three types of animation configurations that you have access to out of the box with Animated. They are `decay`, `spring`, and `timing`. Again, all three of these allow you to transform a specific value, but  each differ in how that value is transformed: "decay" will start with an initial velocity and gradually slow to a stop, "spring" provides a  normal spring type of animation, and "timing" animates a value of a  specified time. 

Let's take a look at some of these in action!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/H1LJ3C8yzuc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=429" id="widget430" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/7a701a6fbe7d0331e3ae8cce7899d55ce9653bd3)



> ## ⚠️ Cautions: Animations ⚠️

> Once you fully grasp the Animated API, a whole new world will open up to you. It sounds great, but this can be a double-edged sword. It's a  great thing because you now have the ability to enhance the feel of your application with animations. However, with great power comes great  responsibility. 

> The goal of having animations is to add to the user's experience, not distract from it. By keeping this in mind whenever you're adding  animations to your app, not only will your app perform better -- you'll  also minimize the risk of ruining your user's experience with  unnecessary animations.



### Quiz Question

Animated comes with three built in animation configurations. Please select all that apply: 

- 

##### Time for a *quick* check-in!

Task List

- 

## Summary

In this section we learned how to improve your application's UX by using React Native's `Animated` library to add thoughtful animations. For more reading on Animated, you can view the [official documentation](https://facebook.github.io/react-native/docs/animated.html).