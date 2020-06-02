# 2. Tab Navigator



> ## 💡React Navigation v2💡
>
> The videos in this course cover React Navigation v1. Recently, an updated version of React Navigation was released. [Here](https://reactnavigation.org/blog) are some of the main differences between these two versions. The documentation for version 1 is located [here](https://v1.reactnavigation.org/), and the documentation for version 2 is [here](https://reactnavigation.org/). The default version shipped with `npm` is v2, so if you want to use v1, you'd have to specify that in your `package.json` file.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/SfdRg-bMfLc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=389" id="widget390" width="640" height="360" frameborder="0"></iframe>



## Tab Navigator v1

By using `TabNavigator`, users can navigate through different screens within an application simply by pressing tabs that render different components. 

## Tab Navigator v2

`TabNavigator` is deprecated in favor of [`createBottomTabNavigator`](https://reactnavigation.org/docs/en/tab-based-navigation.html). [`createMaterialTopTabNavigator`](https://reactnavigation.org/docs/en/material-top-tab-navigator.html) and [`createMaterialBottomTabNavigator`](https://reactnavigation.org/docs/en/material-bottom-tab-navigator.html) are also available as options for Android. Please note that `createBottomTabNavigator` does not support the `animationEnabled` and `swipeEnabled` properties.



Let's see how we'd use Tab Navigator v2.

Say we have two basic functional components that just render some text, `Hello` and `Goodbye`:

```js
const Hello = () => (
  <View>
    <Text>Hello!</Text>
  </View>
);

const Goodbye = () => (
  <View>
    <Text>Goodbye!</Text>
  </View>
);
```

If we want to add two tabs for users to select (one rendering `Hello`, the other rendering `Goodbye`), first we'll need to install `react-navigation` and then import `createBottomTabNavigator`:

```
yarn add react-navigation
```

or

```bash
npm install --save react-navigation
import { createBottomTabNavigator } from 'react-navigation';
```

Once this is done, we can pass an object into `createBottomTabNavigator` like so:

```js
const Tabs = createBottomTabNavigator({
  Hello: {
    screen: Hello
  },
  Goodbye: {
    screen: Goodbye
  },
});
```

Inside the object, each key-and-value pair represents a single tab. The keys represent the *name* of the tab; this is what users will see and press. Note that a `screen` property is included as well; this is the component that is rendered when the tab is active.

Here comes the interesting part: what `createBottomTabNavigator` returns is actually a *component*! Since we have stored this in a `Tabs` variable, we can just render this as we would with any component:

```js
// App.js

// ...

export default class App extends React.Component {
  render() {
    return (
      <Tabs />
    );
  }
}
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/4Ki4UbOy8II?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=391" id="widget392" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/9ff26370e4e5593195fdcad4d85e74f540a39220)

![image-20200519134610137](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson4-Navigation\images\2-quiz)

> The Tab Navigator is just one of React Navigation's three basic  customizable navigators. We'll take a look at the other two later in  this Lesson!



## StatusBar

Recall that so far, our application has been using arbitrary `padding` to account for the status bar at the top of the device's screen. Let's  go ahead and change that! React Native actually provides a simple `StatusBar` component to customize how the status bar appears in an application.

Before we take a look at how to implement `StatusBar`, be sure to import it from `react-native`:

```js
import { StatusBar } from 'react-native';
```

Let's jump in!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/LzLIqKtjpD8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=393" id="widget394" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/b5a0e8840cbc48486056331cd92399b729700b56)



##### We've just made it possible for users to navigate between different screens. How are things looking?

Task List

- 









## Summary

React Navigator v1 offers a `TabNavigator` (and React Navigator v2 offers us `createBottomTabNavigator`) API that allows for navigation between different screens via individual tabs. Each tab is dedicated to rendering a specific component.

This section also detailed React Native's `StatusBar` component. `StatusBar` is relatively straightforward to use and is fully customizable -- we typically just set properties to change it!

In the next section, we'll take a look at React Navigator's Stack  Navigator, which allows users to add and remove screens from a stack.

### Further Research

- [StatusBar props](https://facebook.github.io/react-native/docs/statusbar.html#props) from the React Native docs
- [TabNavigator v1](https://v1.reactnavigation.org/docs/tab-navigator.html) from the React Navigator docs
- [TabNavigator v2](https://reactnavigation.org/docs/en/bottom-tab-navigator.html) from the React Navigator docs