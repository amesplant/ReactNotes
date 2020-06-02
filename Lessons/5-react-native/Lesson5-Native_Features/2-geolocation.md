# 2. Geolocation



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/ynXUEGUVGA8?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=415" id="widget416" width="640" height="360" frameborder="0"></iframe>



A common feature of native applications is the ability to access and  receive updates about the user's current location. Like most things,  Expo makes this rather straightforward by giving us a JavaScript API  that will work on both iOS and Android. 

```js
import { Location } from 'expo';
```

Typically when dealing with location services, there are one of two  features you'll need: getting the user's current location, or getting  and *watching* the user's current location for updates. Expo's `Location` property gives us both of these options with `getCurrentPositionAsync` and `watchPositionAsync`. 

`getCurrentPositionAsync` gets the current location of the device, without watching for future updates. `watchPositionAsync` will also get the current location of the device, but it will also  subscribe to location updates. This way, you'll be notified if that  device moves location.

For the full documentation on how to use Expo's `Location` property, visit [Location](https://docs.expo.io/versions/latest/sdk/location.html)



> ## 💡 Geolocation Tips 💡
>
> Whenever you're dealing with a feature that requires the user's  permission to work properly, it's important that you account for all the different UI options that could be shown. For example, when dealing  with a user's location, there are three scenarios to manage:
>
> 1. The user gives you permission to view their location (best-case scenario). 
> 2. The user decides to neither deny nor grant you permission to their location. 
> 3. The user denies giving you access to their location. 
>
> In an ideal world, the user would always grant you permission to  whatever you'd like, but, this isn't always the case and as a UI  developer, you need to plan accordingly for those moments.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/nIQMG9N33IE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=417" id="widget418" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/62780584135dbfcee999b10ec3f01ec646aeb27b)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/B56Uz-NKKhs?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=419" id="widget420" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/70aa708e381b86471da886e01efc6568df076c54)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/oiz4Fn1Iqqk?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=421" id="widget422" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/5a834dc7790f3612a9bebdf4b25ded34e9bfe580)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/BNYvgnCvPFc?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=423" id="widget424" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/654fab8ad1502c104a0501adea1819a4f9ab54c1)

Be sure that you have included the following imports: in `Live.js`:

```js
import { Location, Permissions } from 'expo';
import { calculateDirection } from '../utils/helpers';
```



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/tl8blRR_nc0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=425" id="widget426" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/0b092b57b530fd6b2d9e9577dd299351e74df75f)

**Note**: If you are running into errors with the code in this commit, update the initial value of the `Live`'s state's `coords` property to a non-`null` value.

![image-20200523095314348](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson5-Native_Features\images\2-quiz)

> To subscribe to a user's location, you use Expo's `Location.watchPositionAsync` method passing it two arguments: an options object, and a callback to be called whenever the location changes.

## Summary

In this concept, we saw how to use Expo's `Location` property to watch the user's current location using `watchPositionAsync`. For further reading, feel free to check out the [official documentation](https://docs.expo.io/versions/latest/sdk/location.html).