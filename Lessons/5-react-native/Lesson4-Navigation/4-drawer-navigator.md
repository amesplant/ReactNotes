# 4. Drawer Navigator



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/rxb47NRwix8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=407" id="widget408" width="640" height="360" frameborder="0"></iframe>



## Drawer Navigator v1

React Navigation offers one more basic navigator to create custom navigation through React Native apps: the `DrawerNavigator`. While `TabNavigator` uses tabs to help users navigate to specific screens, `DrawerNavigator` uses a drawer-like menu that slides in from the side of the screen.  While we won't be implementing this into UdaciFitness -- it's still  important to know and fairly common in React Native applications!

To use `DrawerNavigator`, be sure to install version 1 of `react-navigation` and import the following from `react-navigation`:

```
import { DrawerNavigator } from 'react-navigation';
```

Luckily, many of the same philosophies shared by `StackNavigator` and `TabNavigator` apply here as well! Let's check out two basic components again and see how `DrawerNavigator` renders them:

```js
const Home = ({ navigation }) => (
  <View>
    <Text>This is the Home view</Text>
    <TouchableOpacity onPress={() => navigation.navigate('DrawerOpen')}>
      <Text>Press here to open the drawer!</Text>
    </TouchableOpacity>
  </View>
);

const Dashboard = ({ navigation }) => (
  <View>
    <Text>This is the Dashboard view</Text>
    <TouchableOpacity onPress={() => navigation.navigate('DrawerOpen')}>
      <Text>Press here to open the drawer!</Text>
    </TouchableOpacity>
  </View>
);
```

Note that rather than routing to another component, each `TouchableOpacity` wrapper opens the drawer. Likewise, `'DrawerClose`' can be used to close the drawer. To simplify things, React Navigation also offers `'DrawerToggle'` to automatically select which navigation is appropriate based on the current drawer state.

Similar to `TabNavigator` and `StackNavigator`, we can then pass an object into `DrawerNavigator`, render the component returned, and we're all set!

```js
const Drawer = DrawerNavigator({
  Home: {
    screen: Home
  },
  Dashboard: {
    screen: Dashboard
  }
});
// App.js

// ...

export default class App extends React.Component {
  render() {
    return (
      <Drawer />
    );
  }
}
```



## Drawer Navigator v2

`DrawerNavigator` has been deprecated in favor of [`createDrawerNavigator`](https://reactnavigation.org/docs/en/drawer-navigator.html), which  is functionally identical but clearly communicates that it's a function that returns a component. 

According to the documentation:

> [Rather than opening a drawer with `navigation.navigate(‘DrawerOpen’)`, you can now call `navigation.openDrawer()`. Other methods are `closeDrawer()` and `toggleDrawer()`.](https://reactnavigation.org/blog/)

![image-20200519141757948](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson4-Navigation\images\4-quiz-1)

> Many native applications include a drawer menu to help users navigate  through the app. The Drawer Navigator offers us a simple but powerful  way to implement that in React Native apps!
>

### ![image-20200519141954077](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson4-Navigation\images\4-quiz-2)



### Component

Screens are rendered and placed on top of one another

Screens are switched by using a tab bar

Screens are switched by a menu that slides in from the side

## Summary

React Navigation's Drawer Navigator is used to easily set up a screen with drawer navigation. Many of the same practices we use to set up the Stack Navigator and the Tab Navigator apply to the Drawer Navigator as  well. Simply pass in an object containing the different screens, and the return value is a component ready to be rendered. As a result, this  makes Drawer Navigator components easy for nesting with other  navigators!

### Further Research

- [DrawerNavigator v1](https://v1.reactnavigation.org/docs/drawer-navigator.html) from the React Navigator docs
- [DrawerNavigator v2](https://reactnavigation.org/docs/en/drawer-navigator.html) from the React Navigator docs