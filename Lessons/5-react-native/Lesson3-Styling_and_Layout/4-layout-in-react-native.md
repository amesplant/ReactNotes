# 4. Layout In React Native



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Yl69abRLGbY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=359" id="widget360" width="640" height="360" frameborder="0"></iframe>



## React Native's Flexbox Implementation

React Native implements flexbox for build layouts, but there are some key differences to keep in mind as you develop your applications.  First, all containers in React Native are *flex containers* by default. Recall that in traditional CSS flexbox, you would normally define a flex container like so:

```css
/*example.css*/

.container {
  display: flex;
}
```

However, this is completely *unnecessary* in React Native! By default, everything is `display: flex;`. You can just use the defaults as they are, without adding different properties or writing extra code.

Another important distinction is how React Native handles `flex-direction`, a property that establishes the main axis (i.e., defining the direction in which flex items are placed). In web applications, items default to `row`. But since we're working on mobile devices, React Native sets the default to `column`, which lays out items *vertically*.

One more major difference you'll encounter is how the `flex` property is used. On the web, `flex` specifies how a flex item grows or shrinks to manage the space around it (along the main axis). In React Native, `flex` is generally used with flex items that are on the same level, but hold different `flex` values. For example:

```js
import React from 'react';
import { View } from 'react-native';

const FlexDemo = props => (
  <View style={{flex: 1}}>
    <View style={{flex: 1, backgroundColor: 'red'}} />
    <View style={{flex: 2, backgroundColor: 'green'}} />
    <View style={{flex: 3, backgroundColor: 'blue'}} />
  </View>
);

export default FlexDemo;
```

Here, `FlexDemo` is a stateless functional component which renders `` components with different `flex` values. Its outermost container is set to `flex: 1`, which will expand the full available width along the main axis (i.e., the entire screen in this example). Its children `` components will fill the space accordingly, rendering a `blue` background color that takes up three times as much space as `red` takes, and `green` that takes up exactly twice as much space as `red` takes.



## Other Differences

In addition to the above, here is a list of defaults in other common CSS properties that React Native applies to components:

```css
box-sizing: border-box;
position: relative;
align-items: stretch;
flex-shrink: 0;
align-content: flex-start;
border: 0 solid black;
margin: 0;
padding: 0;
min-width: 0;
```

![image-20200517092439020](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson3-Styling_and_Layout\images\4-quiz)

> While lots of the same philosophies of flexbox apply to both web and  React Native apps, there are some distinct differences with how React  Native implements flexbox.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/6ZgAFY6Lakg?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=361" id="widget362" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/4b145ff1126a60b026aaffc72970f46c5e8692d2)



## Platform API

Recall that React's approach to app development is "learn once, write anywhere." The goal is to use the same principles, technologies, and in the case of React Native -- the same *code* -- to develop applications. However, there may be cases that make sense to use *distinct* code for each mobile platform. For example, what if we wanted unique styling between iOS and Android visual components? 

React Native gives us a convenient way to organize and separate code through the `Platform` API. Let's check out an example!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/KtATaKs7qjQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=363" id="widget364" width="640" height="360" frameborder="0"></iframe>



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/vBIDOsEkUK8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=365" id="widget366" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/c5c645478a1f631f7851463b80e216289b17b4d4)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/pW-iEnKf7Og?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=367" id="widget368" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/2c0d0b9ef0b36f53d793ae1452d2d20857bd9d96)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/nm8mq8__U8Q?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=369" id="widget370" width="640" height="360" frameborder="0"></iframe>



> ## 💡 `Dimensions` API💡
>
> React Native also comes with [Dimensions](https://facebook.github.io/react-native/docs/dimensions.html), which allows you to select window's width and height in the user's device!
>
> First, make sure you pull the API from React Native:
>
> ```js
> import { Dimensions } from 'react-native';
> ```
>
> Then, you can simply grab the window sizes with the Dimensions API's `get` method:
>
> ```js
> const { width, height } = Dimensions.get('window');
> ```
>
> Feel free to use these measurements to, for example, plan how your ``s will look.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/4edBztoh2rk?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=371" id="widget372" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/f2f0342661d87060376bf54c425793b4c3b239c9)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/6qWrHcBJF3c?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=373" id="widget374" width="640" height="360" frameborder="0"></iframe>



To install our calendar, run `yarn add udacifitness-calendar`.



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/57d249307036bc97c8b539fc3b5fcc38455a3419)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/t53XoUg4Dr4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=375" id="widget376" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/556a167f9f773c128c6d982c27130fe7b0b27d82)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/z8IKGR5pmGM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=377" id="widget378" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/cdcef7571fecac412cdb1995538114b0f36a91c7)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/0MY2yNuMiBg?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=379" id="widget380" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/1cc6fd9ce59e9acf6012aa5800b872ac98b5e209)



##### The layout is nearly complete! One more check-in before the next section.

Task List

- 



















## Summary

React Native uses **flexbox** to manage layout in mobile applications. However, there are some minor distinctions between the  official flexbox specification (i.e., CSS *on the web*) and React Native's own implementation. Most of these distinctions are just differences in default settings.

Since differences also exist in how Android and iOS applications should look and feel, React Native also offers a `Platform` API, which we can leverage to style each platform independently. 

In the next section, we'll take a look at some common "gotchas" and best practices when styling components. 

### Further Research

- [Understanding React Native flexbox layout](https://medium.com/the-react-native-log/understanding-react-native-flexbox-layout-7a528200afd4)
- [Platform Specific Code](https://facebook.github.io/react-native/docs/platform-specific-code.html) from the React Native docs