# 3. Common React Native Components



## Common React Native Components



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/9Nt1tXV3y0c?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=299" id="widget300" width="640" height="360" frameborder="0"></iframe>



When writing HTML, we're used to using `` and `` tags to define sections or to contain other elements on the page. In  React Native, a similar principle applies, but this time we're using  React Native's `` component to build the application UI. Just like HTML's ``, `` components can accommodate several props (e.g. `style`), and can even be nested inside other `` components!

`` works just how you'd expect, as well. Its main objective is to, by no surprise, render text in the application. Just like ``, styling and nesting capabilities apply to `` components, as well.

Let's see how they work!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/_Qv4NGKNuug?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=301" id="widget302" width="640" height="360" frameborder="0"></iframe>



## In-Class Project Overview



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/HZSi_XB3drA?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=303" id="widget304" width="640" height="360" frameborder="0"></iframe>



## Icons



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/tYb0-l81x4U?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=305" id="widget306" width="640" height="360" frameborder="0"></iframe>



Right out of the box, **Create React Native App** offers support for thousands of vector icons to use in your applications. Feel free to bookmark and check out Expo's [vector icon directory](https://expo.github.io/vector-icons) for a complete list. Whichever icon set you choose, just be sure that  it fits the overall look and feel of your application (e.g., using  platform-specific icons).



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/sH4D8b7MotQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=307" id="widget308" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/WtAiZNpKpkM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=309" id="widget310" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in the previous two videos.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/c3b244a93a6fdd484cfd9306fc05e0c2095bdbe4)

> ## ⚠️  Icons not Rendering? ⚠️
>
> In the commit above, the `color` property of the `MaterialIcons` component is set to `white`. This will make it seem as if no icons are appearing, since the  background color is also white. Feel free to switch this value to `black` (as the above video demonstrates).





<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/DrUMM2IzL9Q?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=311" id="widget312" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/f710aa25881665feacf82b100643146b8d011446)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/xLh5C-hCuSE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=313" id="widget314" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/3aa3f69d21b8a96b4b9d99f67b655772a479095f)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/s0X1NrNNVQM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=315" id="widget316" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/a7ab15bf3f46d1202d86a2c2fe06e458bd7faffd)



## Touchables

Users mainly interact with web apps with *clicks*. In the world of mobile apps, however, several different *touch* gestures are used to navigate through the app: tapping a button, swiping to scroll through a list, and so on. 

React Native offers a number of components to handle "tapping gestures," or what is called **Touchables**. Let's take a look at them in detail in the following video:

- `Button`
- `TouchableHighlight`
- `TouchableOpacity`
- `TouchableNativeFeedback`
- `TouchableWithoutFeedback`



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/u2-Efn5K6eM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=317" id="widget318" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/7OzFooD9EoM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=319" id="widget320" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/fea2dbb62ef103ed0a44307dd7922bdfcab83ef2)

![image-20200516165912992](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson2-React_vs_Reactive_Native\images\3-quiz-1)

> Both Buttons and Touchables allow us to handle some tapping gestures in  our apps. Buttons render nicely out-of-the-box, but feel free to  incorporate components such as `TouchableHighlight` or `TouchableOpacity` to provide more nuanced feedback for your users.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/eLrjkwYIB0g?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=321" id="widget322" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Mg8vSOPiQ7M?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=323" id="widget324" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/528c326cc0dfafcd74199c7be9cb00d971cc8a23)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/cb3vt0Gpbjc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=325" id="widget326" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/f9b86f4b8fd5c2c2c89cfa32552b67f76a48fcf3)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/b-AXsdbqZyU?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=327" id="widget328" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/a45a7c370228aaa333840544c508c7d8d9f7da31)



> ## 💡 Pause Udacifitness💡

> At this point, let's put the UdaciFitness project on hold for a bit and talk about some other common React Native components.  For example, how would you handle lists in a mobile app? What about forms, or images? 

> Though these are not necessarily used in the in-class project, these  components are still great to know as you develop React Native  applications.



## Lists

React Native comes with a few ways to render lists. You'll probably run into `ScrollView` and `FlatList` components most commonly, so let's take a look at both of these in detail!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/6JgdIxDn8H4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=329" id="widget330" width="640" height="360" frameborder="0"></iframe>



> ## 💡 Seeing Errors with `ScrollView`? 💡

> If you're running into errors mentioning that *`ScrollView` has no propType...*, we recommend reinstalling Create React Native App globally, as well as  updating the Expo mobile application. If you still find issues, feel  free to check out this [GitHub issue](https://github.com/facebook/react-native/issues/16090) on the official React Native repo.



> ## 💡 `SectionList` 💡

> What if you wanted to add section headers to a list? `FlatList` doesn’t quite support these, but React Native offers another list  component that renders these headers nicely. Feel free to check out [SectionList](https://facebook.github.io/react-native/docs/sectionlist.html) in the React Native documentation for a closer look

![image-20200516192302031](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson2-React_vs_Reactive_Native\images\3-quiz-2)

> Fantastic! You have many choices for rendering lists in React Native, so feel free to choose the one best suited for your application.

## Forms

Forms in React Native are just like the forms in React that you  already know: the state of input form elements is controlled by the  React component that renders that form. That is, form values are held in local component state, making state the "source of truth" for that  form.

React Native provides a few basic components to use in your  application's forms. We'll take a look at each of these more closely in  the following video:

- `TextInput`
- `KeyboardAvoidingView`
- `Slider`
- `Switch`



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/WxdnpxrWZkI?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=331" id="widget332" width="640" height="360" frameborder="0"></iframe>



> ## ⚠️ Oops! (`onChange` vs. `onChangeText`) ⚠️

> In the above video, `App` renders a `TextInput` component with an `onChange` prop. With the way that the event handler, `handleTextChange()`, is implemented, the prop should be `onChangeText`. 

> While both methods are invoked on value change, `onChangeText` passes the actual value (text) as the argument. On the other hand, `onChange` passes the entire event object as an argument. Both are perfectly valid props, but the logic of your event handler will need to be tailored to  the prop chosen. For more info, check out [this post](https://stackoverflow.com/questions/44416541/react-native-difference-between-onchange-vs-onchangetext-of-textinput) on Stack Overflow.



![image-20200516192913265](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson2-React_vs_Reactive_Native\images\3-quiz-3)



> `KeyboardAvoidingView` solves the problem of views that would otherwise block the way of a virtual keyboard.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/uxbqKJchzKQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=333" id="widget334" width="640" height="360" frameborder="0"></iframe>



## Other Components

We've just seen some of the most important components built into  React Native. These components will get you started with the essential  functionalities in the apps that you build -- but the list of available  components goes on! Feel free to review the React Native documentation  for a [complete list](https://facebook.github.io/react-native/docs/components-and-apis.html#components-and-apis). For starters, we recommend checking out:

- [ActivityIndicator](https://facebook.github.io/react-native/docs/activityindicator.html)
- [Picker](https://facebook.github.io/react-native/docs/picker.html)
- [WebView](https://facebook.github.io/react-native/docs/webview.html)
- [Modal](https://facebook.github.io/react-native/docs/modal.html)

Note that certain components are also platform-specific! Though you want to build cross-platform components with *composition*, reusing as much code as possible, it may make sense for certain  elements to be different depending on your audience (i.e., iOS vs.  Android).



## Summary

React Native provides a variety of built-in components for developing mobile applications. While some support basic functionality in an  application (e.g., text, images, lists), others offer more specialized  functionality (e.g., pulling to refresh, displaying a loading  indicator). Feel free to check out [Components and APIs](https://facebook.github.io/react-native/docs/components-and-apis.html) in the React Native documentation for an exhaustive list.