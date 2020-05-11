# 3. Folder Structure



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/4Ud2n_ceUZc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=209" id="widget210" width="640" height="360" frameborder="0"></iframe>



Right now, all of our app's code is located in a single file. This isn't a  very realistic way to build an app, though. Hopefully it hasn't been too frustrating scrolling up and down and up and down to find the right  place to add your code! 😉

To fix this, we're going to use Create React App to scaffold out a  React app for us. If, for some reason, you don't have Create React App  installed on your machine, you can install it by running the following  in your Terminal:

```bash
npm install -g create-react-app
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/QzBtsjxouyw?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=211" id="widget212" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/5c9b7e4b84d005de1139620f4d795bc5eacd95ca)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/JnBpKGOqqwc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=213" id="widget214" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/371d896c07230ffb1b056233e605f8079c4e32f9)





<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/N-44Rn9B8QY?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=215" id="widget216" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/4a89382786d9516a41415965a9172b9853d8998f)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/sgRSJuKLB8g?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=217" id="widget218" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/6da37ad5d09edc5d06c00250d03b578ea4bdbcb7)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/zu_OuldiJw4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=219" id="widget220" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/7a540c1ba3f6c0a3e0a249b76584c5c215a99604)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/hC6WWIXVlSo?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=221" id="widget222" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/1177c07de724399ba9f8b1573c4c9711caa23daa)



## "Rails-style" Organization

To recap, we've organized the individual elements of our app with a  "Rails-style" approach. That is, assets are grouped by "type" or  "capability": any action will be found in the *Actions* folder, any reducer will be found in *Reducers*, and so on. In fact, the “real world” example from [Redux on GitHub](https://github.com/reactjs/redux/tree/master/examples/real-world) structures the app this very way. Under this directory structure, if we wanted to import all actions into a component, we can get them all in a single import!

```text
Frontend
   - Components
      - component1.js
      - component2.js
      - component3.js
   - Actions
      - action1.js
      - action2.js
   - Reducers
      - reducer1.js
   - Util
   - Store
```



# Other Patterns

Along with the "Rails style" of organizing your folder structure, you may find other approaches that developers use to build their directory  more to your liking. An alternative way to structure the same  application, then, is by feature:

```text
├── dashboard
│ ├── actions.js
│ ├── index.js
│ └── reducer.js
└── nav
 ├── actions.js
 ├── index.js
 └── reducer.js
```

This form of organization groups assets by their common feature or  “concept.” That is, all assets related to a navigation component are all together in a single, modular folder. It’s a great way to visually  express what the application is all about. However, if the app contains  several hundred components, it can become more difficult to navigate  through.

What's more: you might even see that some developers prefer a ["duck" style](https://medium.freecodecamp.org/scaling-your-redux-app-with-ducks-6115955638be) approach, where Redux and state management files are completely separated from files that render UI.

Ultimately, the choice is yours. Whichever way you choose to organize your directory structure, just be sure that it’s something that makes  sense for your app, and it’s something you’re comfortable with!



# Summary

This section didn't accomplish anything with React or Redux. All we  did here was improve the structure and organization of our app by moving each portion of the app to a specific folder structure. 

To say it one more time, there's no "right" way to build out the  folder structure for you app. However, doing it this way is handy  because we're using the structure provided by Create React App. Using  this structure, it's easy to convert a plain React application over to  one that includes Redux. Another benefit is that other React developers  will already be comfortable with this file/folder organization.