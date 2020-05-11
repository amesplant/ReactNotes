# 4. Planning Stage: Step 3 - Determine Events In The App



# Determine What Events Happen in the App

We need to take a look at *what* is happening in each component. Let's determine what actions the app or the user is performing **on the data**. Is the data being set, modified, or deleted?...then we'll need an action to keep track of that event!

Let's *italicize* the action and **bold** the data.

# Tweets List Component



[![img](https://video.udacity-data.com/topher/2018/March/5abd5744_nd019-redux-l7-store-01-tweet-list/nd019-redux-l7-store-01-tweet-list.png)The Tweets List Component ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/bb335fa7-c62b-432f-96d0-fdacf739ce1c#)



For the Tweets List component, the only information that we see is that  we'll have to get a list of all of the tweets. So for this component, we just need to:

- *get* the **tweets**

So the action type for event this will probably be something like `GET_LIST_OF_TWEETS` or `GET_DATA`.



# Tweet Component



[![img](https://video.udacity-data.com/topher/2018/March/5abd5771_nd019-redux-l7-store-02-tweet/nd019-redux-l7-store-02-tweet.png)The Tweet Component ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/bb335fa7-c62b-432f-96d0-fdacf739ce1c#)



- We *get* a particular tweet from a list of **tweets**.
- We *get* the **authedUser (user that is currently logged in)** so the user can *toggle* the likes on each **tweet**.
- We *get* the **authedUser** so the user can *reply* to a **tweet**.



# Tweet Container Component



[![img](https://video.udacity-data.com/topher/2018/March/5abd578d_nd019-redux-l7-store-03-tweet-container/nd019-redux-l7-store-03-tweet-container.png)The Tweet Container Component ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/bb335fa7-c62b-432f-96d0-fdacf739ce1c#)



- We *get* a specific tweet from a list of **tweets**.
- We *get* the replies to a specific tweet from a list of **tweets**.



# New Tweet Component



[![img](https://video.udacity-data.com/topher/2018/March/5abd57a6_nd019-redux-l7-store-04-new-tweet/nd019-redux-l7-store-04-new-tweet.png)The New Tweet Component ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/bb335fa7-c62b-432f-96d0-fdacf739ce1c#)



- We *get* the **authedUser** so the user can *create* a new **tweet**.
- We *set* the **text of the new tweet**.

Let's move on to Step 4, where we'll determine which of the data above will live in the store.