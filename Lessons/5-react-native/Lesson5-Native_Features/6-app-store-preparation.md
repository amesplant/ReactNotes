## 6. App Store Preparations



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/_tyCx2yAkc0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=441" id="widget442" width="640" height="360" frameborder="0"></iframe>



When you submit an app to either app store, there is more information you  need to submit than just the app itself. For example, you need details  such as the app description, icon, etc. Luckily for us, Expo make it  easy to specify these sorts of things just by editing the `app.json` file at the root of our app folder. Here's an example of configurations we'll be adding in our UdaciFitness app:

```js
{
  "expo": {
    "sdkVersion": "19.0.0",
    "orientation": "portrait",
    "name": "Udacifitness",
    "description": "The best triathlon training app in the world.",
    "slug": "udacifitness",
    "version": "1.0",
    "icon": "https://maxcdn.icons8.com/Color/PNG/512/Sports/triathlon-512.png",
    "notification": {
      "icon": "http://www.student-scholarships.com/images/made/img/featured/nav_basketball_45_45.png"
    },
    "ios": {
     "bundleIdentifier": "org.udacifitness.exp",
    },
    "android": {
     "package": "org.udacifitness.exp",
    }
  },
}
```

Let's go ahead and add this to our app!



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/4rcPX-bIneE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=443" id="widget444" width="640" height="360" frameborder="0"></iframe>

![image-20200519143042714](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson5-Native_Features\images\6-quiz)

> Good work! When you create an app with `create-react-native-app` you'll automatically have an app.json file created for you, which will contain all of the configuration settings for your app.

## What are .apk and .ipa Files?

Before you submit your application to either app store, you need to  "package" it appropriately. The iOS App Store will ask you for a *.ipa* ("iOS App Store Package") file and the Android Google Play store will ask you for a *.apk* ("Android Application Package") file. When you create either an ipa or a apk file, you're essentially creating a bundle of all of the necessary  information that either App store needs in order to process and run your application. 

The easiest way to generate both the .apk and the .ipa files is to use Expo's `exp` CLI. First, run `npm install -g exp`. Once that's installed (and after you've configured your `app.json` file), you can run `exp build:ios` to build your .ipa file, and `exp build:android` to build your .apk file.

Note that these will take anywhere from 10-20 minutes to build, so  you'll need to be patient. To check the status of the build you can run `exp build:status`. Eventually that command will give you a URL where you can go to download either your .ipa or .apk files.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/IryVgEQ0SvE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=445" id="widget446" width="640" height="360" frameborder="0"></iframe>



> ## ⚠️ The Rest of the Way ⚠️

> The hardest part about uploading your application to either app store is generating a .ipa or .apk file. Because we covered that in the  previous section, we're not going to cover the entire process of  actually uploading your app. The following documents should help you:  for iOS, [Uploading a Build for an App](https://developer.apple.com/library/content/documentation/LanguagesUtilities/Conceptual/iTunesConnect_Guide/Chapters/UploadingBinariesforanApp.html#//apple_ref/doc/uid/TP40011225-CH38-SW1) and for Android, [Upload an App](https://support.google.com/googleplay/android-developer/answer/113469?hl=en).



## Summary

In this section we learned about preparing your application for the  app store and generating .apk and .ipa files. For further reading, feel  free t ocheck out [Building Standalone Apps with Expo](https://docs.expo.io/versions/latest/guides/building-standalone-apps.html)