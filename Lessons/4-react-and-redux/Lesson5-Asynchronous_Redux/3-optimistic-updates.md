# 3. Optimistic Updates

When dealing with asynchronous requests, there will always be some  delay involved. If not taken into consideration, this could cause some  weird UI issues. For example, let’s say when a user wants to delete a  todo item, that whole process from when the user clicks“delete” to when  that item is removed from the database takes two seconds. If you  designed the UI to *wait for the confirmation from the server* to remove the item from the list on the client, your user would click  “delete” and then would have to wait for two seconds to see that update  in the UI. That’s not the best experience.

Instead what you can do is a technique called **optimistic updates**. Instead of waiting for confirmation from the server, just instantly  remove the user from the UI when the user clicks “delete”, then, if the  server responds back with an error that the user wasn’t actually  deleted, you can add the information back in. This way your user gets  that instant feedback from the UI, but, under the hood, the request is  still asynchronous. 

We’ll see this technique in the upcoming screencasts. 



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/l-wRpOTFOys?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=159" id="widget160" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/5186502ac6461c2e88ba1dbf1ec158764c84823c)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/7nicdmL-1k4?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=161" id="widget162" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/89a31404efd2482256e4ce4fbf698fee4afda100)



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/-uooq_C6jqM?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=163" id="widget164" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-redux-todos-goals/commit/d4732ee5af9cf1ee87b5bd42ec46034b38de4aa3)



# Summary

In this section, swapped more functionality over to using the API. We now use the database to:

- remove Todos and Goals
- toggle the state of a Todos
- save a new Todo or Goal

What's important is that for the removing and toggling, we're doing these actions *optimistically*. So we're assuming the change will succeed correctly on the server, so  we update the UI immediately, and then only roll back to the original  state if the API returns an error. Doing optimistic updates is better  because it provides a more realistic and dynamic experience to the user.