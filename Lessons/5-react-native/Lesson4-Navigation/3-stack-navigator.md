# 3. Stack Navigator



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/uMbBR5nu3eg?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=395" id="widget396" width="640" height="360" frameborder="0"></iframe>

## Stack Navigator v5

> https://reactnavigation.org/
>
> This course introduces you to v1 and v2, which are really old by now!







## Stack Navigator v1

When pressing an item in, say, an index view, we expect to go to a  new screen with details on that item. React Navigation offers another  navigator to do just that! With `Stack Navigator`, new screens are added and removed as a *stack*. This places screens on top of one another in a "last in, first out" manner, similar to `Array`'s `push()` and `pop()` methods.

`StackNavigator`'s usage is largely similar to that of `TabNavigator`. But rather than passing in an object of different tabs, we pass in an  object of the different screens that should be available in that stack.

## Stack Navigator v2

`StackNavigator` has been deprecated in favor of [`createStackNavigator`](https://reactnavigation.org/docs/en/stack-navigator.html), which is functionally identical but clearly communicates that it's a function that returns a component.

According to the [documentation](https://reactnavigation.org/blog/), the new [`StackNavigator`](https://reactnavigation.org/docs/en/stack-navigator.html) is “less pushy”:

> [Each time you call push we add a new route to the navigation stack. When you call `navigate`, it first tries to find an existing route with that name, and only pushes a new route if there isn't yet one on the stack.](https://reactnavigation.org/docs/en/navigating.html)

> [Let's suppose that we actually *want*  to add another details screen. This is pretty common in cases where you  pass in some unique data to each route (more on that later when we talk  about `params`!). To do this, we can change `navigate` to `push`. This allows us to express the intent to add another route regardless of the existing navigation history.](https://reactnavigation.org/docs/en/navigating.html)



Let's see how we'd use the Stack Navigator from React Navigation v2.

First, go ahead an import `createStackNavigator` from `react-navigation`. 

```
import { createStackNavigator } from 'react-navigation';
```

Say we have two basic components, `Home` and `Dashboard`:

```js
const Home = ({ navigation }) => (
  <View>
    <Text>This is the Home view</Text>
    <TouchableOpacity onPress={() => navigation.navigate('Dashboard')}>
      <Text>Press here for the Dashboard</Text>
    </TouchableOpacity>
  </View>
);

const Dashboard = () => (
  <View>
    <Text>This is the Dashboard</Text>
  </View>
);
```

Note that a `navigation` prop is passed to the stateless functional `Home` component, which allows navigation to another route. Once this is done, we can pass an object into `createStackNavigator` similar to how we did for `createBottomTabNavigator`:

```js
const Stack = createStackNavigator({
  Home: {
    screen: Home
  },
  Dashboard: {
    screen: Dashboard
  }
})
```

The return value of passing an object into `createStackNavigator` is a component as well, and we can render it as such!

```js
// App.js

// ...

export default class App extends React.Component {
  render() {
    return (
      <Stack />
    );
  }
}
```

[Stack Navigator](https://reactnavigation.org/docs/en/stack-navigator.html) and [Tab Navigator](https://reactnavigation.org/docs/en/bottom-tab-navigator.html) often go hand-in-hand. Since they each return *components*, you'll often see one nested within the other. Let's see this in action as we implement this into UdaciFitness!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/PkoZ__6NPE8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=397" id="widget398" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/86af918722052eebafbc2892b6cd772b51a18dd4)



![image-20200519135724578](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson4-Navigation\images\3-quiz)

> The Stack Navigator keeps things simple, but is incredibly powerful. We  simply define all screens within an object, pass it into `createStackNavigator`, and it returns a component we can render!

<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/JosvkjGlt30?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=399" id="widget400" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/7d4fba6fba7e0f9833e9645c2f34e9c058c9feed)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/-c5FZCh5LNo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=401" id="widget402" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/5d77f8d831e170fc0ffdeae1bc92a0825e71e14a)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Hv_EbcrmbDY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=403" id="widget404" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/7b2103a06e2394f938168d9f1040dd6ba9ac2e2d)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/_nRJsJ2-zgY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=405" id="widget406" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/18aeee6aac40702c2d86cf976a9a67c5691505cf)



##### Navigation should be good to go at this point! Be sure you have done the following:

Task List

- 













## Summary

React Navigation's Stack Navigator is another customizable navigation option based on adding and removing new screens to a stack. Its API is  similar to that of the Tab Navigator; it takes in an object that defines all screens, then returns a component. Since both the Stack Navigator  and the Tab Navigator both return components, a common practice is to  nest these navigators within one another.

In the next section, we'll take a look at the Drawer Navigator, in  which screens are switched from a drawer that pops out from the side of  the screen!

### Further Research

- [Stack Navigation in React Native](https://medium.com/@swathylenjini/stack-navigation-in-react-native-2cd00374ff3a)
- [StackNavigator v1](https://v1.reactnavigation.org/docs/stack-navigator.html) from the React Navigator docs
- [StackNavigator v2](https://reactnavigation.org/docs/en/stack-navigator.html) from the React Navigator docs