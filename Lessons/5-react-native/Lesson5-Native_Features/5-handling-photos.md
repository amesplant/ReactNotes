## Handling Photos



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/WVCmP3-0_ic?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=437" id="widget438" width="640" height="360" frameborder="0"></iframe>



At this point it shouldn't be a surprise that Expo provides a nice  JavaScript abstraction over the native iOS and Android approaches to  accessing photos from the device's photo gallery. The name of this  property is `ImagePicker` and it does exactly what you would  expect: "Provides access to the system's UI for selecting images from  the phone's photo library or taking a photo with the camera."

We won't be adding any of this functionality to the UdaciFitness app  we're building, but in the next video we will walk through how to use `ImagePicker` just in case you'll need it for a future project. 



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/fAqI8iGAgiQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=439" id="widget440" width="640" height="360" frameborder="0"></iframe>

![image-20200519143655344](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson5-Native_Features\images\5-quiz)

> Nice! To show the UI for the device's image gallery, use the ImagePicker.launchImageLibraryAsync method.

## Summary

In this section, you learned about Expo's `ImagePicker` component to grab images from the phone's photo gallery. For more information, you can read the [official documentation](https://docs.expo.io/versions/latest/sdk/imagepicker.html).