# Local Notifications



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/knsXBVw_U84?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=431" id="widget432" width="640" height="360" frameborder="0"></iframe>



When dealing with notifications, it's important to understand that there are two different types: **push notifications**, and **local notifications**. 

Local notifications do not use or require any external  infrastructure; they happen entirely on the device itself. That means  that the only requirement for the device to display the notification is  that the device is on. On the other hand, push notifications require you to have a server which handles pushing the notification to your user's  devices when a certain event occurs. 

But since we're not incorporating an external server, and all the  logic about when we should show the notification can be done on the  phone itself -- local notifications will be the most ideal for our  application. Let's see how it's done!



> ## ⚠️ Notifications on iOS ⚠️

> Before we jump in, note that with iOS, notifications (both push notifications and local notifications) **do not** appear at the top of the screen automatically if the application is in the foreground. Moreover, push notifications **do not** function in the iOS simulator (whether or not Expo is used).

> For more information, check out [this post](https://forums.expo.io/t/psa-reminder-notifications-in-ios-foregrounded-apps/641) in the Expo forums. This issue does not appear when working with notifications on Android.



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/Qp7OpUgkhsQ?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=433" id="widget434" width="640" height="360" frameborder="0"></iframe>



> ## ⚠️ scheduleLocalNotificationAsync ⚠️

> In the previous video, `scheduleLocalNotificationAsync` should have been used instead of the erroneous `scheduleLocalNotificationsAsync` (note that "Notification" is pluralized in the incorrect version). 

> The following commit contains the correct version in `helpers.js`. For additional information, feel free to check out [this article](https://docs.expo.io/versions/latest/sdk/notifications.html#exponotificationsschedulelocalnotificationasynclocalnotification-schedulingoptions) in the Expo documentation. 



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/blob/setLocalNotification/utils/helpers.js)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/sGdXitMsRTE?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=435" id="widget436" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-UdaciFitness-complete/commit/63778456f674355e40044c673f4b966ebd446866)



![image-20200519144118006](C:\Repos\React Apps (Udacity)\ReactNotes\Lessons\5-react-native\Lesson5-Native_Features\images\4-quiz)

> Nice! To schedule a local notification to be shown in the future you use Expo's `Notifications.scheduleLocalNotificationAsync` method.
>

## Summary

In this section, you learned how to add local notifications to your app using Expo's `Notifications` property. For further reading, you can visit the [official documentation](https://docs.expo.io/versions/latest/sdk/notifications.html).