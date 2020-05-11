# 3. Planning Stage: Steps 1&2 - Break Down Views and Components



# Step 1 - Identify Each View

We need to determine the look and functionality of each view in your  app. One of the best approaches is to draw each view of the app on paper so that you'll have a good idea of what information and data you're  planning to have on each page.

Instead of paper and pencil, you can be a bit more digital and use [software for creating mockups](https://codingsans.com/blog/mockup-tools). If you were given project specifications, check your mock against them  to make sure that you have all of the required features.

For this project, we'll use the screenshots of the app we'll be building instead of mocks.

# View for the Dashboard Page

Let's start by looking at the Dashboard View.

[![img](https://video.udacity-data.com/topher/2018/March/5abd5601_nd019-redux-l7-views-01-dashboard/nd019-redux-l7-views-01-dashboard.jpg)The "dashboard" view displaying the navigation and tweets. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/6bc00d52-4e7a-49e5-9988-a974f627bef1#)



## Dashboard View Requirements

- is located at the home route (`/`)
- shows tweets sorted from most recently added at the top, to oldest at the bottom
- each tweet will show:
  - the author
  - the time stamp
  - who the author is replying to
  - the text of the tweet
  - a reply button - with the number of replies (if higher than 0)
  - a like button - with the number of likes (if higher than 0)



# View for the Tweet Page



[![img](https://video.udacity-data.com/topher/2018/March/5abd5636_nd019-redux-l7-views-02-tweet/nd019-redux-l7-views-02-tweet.jpg)The view for a single tweet. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/6bc00d52-4e7a-49e5-9988-a974f627bef1#)



## Tweet Page View Requirements

- is located at `/tweet/:id`
- shows an individual tweet
  - the author
  - the time stamp
  - a reply button - with the number of replies (if higher than 0)
  - a like button - with the number of likes (if higher than 0)
- has a reply form
- shows all replies 



# View for Creating a New Tweet



[![img](https://video.udacity-data.com/topher/2018/March/5abd5660_nd019-redux-l7-views-03-new-tweet/nd019-redux-l7-views-03-new-tweet.jpg)The view for creating a new Tweet. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/6bc00d52-4e7a-49e5-9988-a974f627bef1#)



## The New Tweet View Requirements

- is located at `/new`
- has a textbox for adding a new tweet



# View Recap

So these are the 3 views we need in our app: 

- Dashboard
- Tweet
- New Tweet

We now have a clear idea of what we're trying to build and can be  confident that our views meet all of the provided requirements.

Now, let's move on to Step 2, where we'll make a conceptual skeleton of our app.



# Step 2: Break Each View Into a Hierarchy of Components

In this step, we'll do 2 things:

- draw boxes around every component
- arrange our components into a hierarchy



## Review Checkpoint

How do you know whether something should be a component in a React app?

According to [Thinking in React docs](https://reactjs.org/docs/thinking-in-react.html#step-1-break-the-ui-into-a-component-hierarchy):

> ...a component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.



### Question 2 of 2

Which of the following are true?

- 

Let's get started by drawing boxes around all of the components and giving them all names. Remember that we have three views:

- Dashboard
- Tweet
- New Tweet

Let's start with the Dashboard view.



# Components for the Dashboard View



[![img](https://video.udacity-data.com/topher/2018/March/5abd56d2_nd019-redux-l7-components-01-dashboard/nd019-redux-l7-components-01-dashboard.png)Dashboard view broken up into Components. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/6bc00d52-4e7a-49e5-9988-a974f627bef1#)



I broke this view into the following React Components:

- **App** - the overall container for the project
- **Navigation** - displays the navigation 
- **Tweets List** - responsible for the entire list of tweets
- **Tweet** - in charge of display the content for a single tweet



# Components for the Tweet View



[![img](https://video.udacity-data.com/topher/2018/March/5abd56f5_nd019-redux-l7-components-02-tweet/nd019-redux-l7-components-02-tweet.png)Tweet view broken up into Components. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/6bc00d52-4e7a-49e5-9988-a974f627bef1#)



I broke this view into the following React Components:

- **App** - the overall container for the project
- **Navigation** - displays the navigation 
- **Tweet Container** - displays a list of tweets
- **Tweet** - displays the content for a single tweet
- **New Tweet** - display the form to create a new tweet (reply)



# Components for the New Tweet View



[![img](https://video.udacity-data.com/topher/2018/March/5abd570f_nd019-redux-l7-components-03-new-tweet/nd019-redux-l7-components-03-new-tweet.png)New Tweet view broken up into Components. ](https://classroom.udacity.com/nanodegrees/nd019/parts/7dab5516-d1ae-45d3-b8f8-d782b5534caf/modules/221d27be-a830-49a3-9803-9aa4a114489c/lessons/f126db7d-157a-4b30-90de-17bd8b07208b/concepts/6bc00d52-4e7a-49e5-9988-a974f627bef1#)



I broke this view into the following React Components:

- **App** - the overall container for the project
- **Navigation** - displays the navigation 
- **New Tweet** - display the form to create a new tweet



# All Components

So from the way I broke things down, the application will have the following components:

- App
- Navigation 
- Tweets List
- Tweet Container
- Tweet
- New Tweet

This component hierarchy tells us which components will be used  inside of other components. It gives us the skeleton of our app. All of  these are presentational components. Right now, we don't care which  components will be upgraded to containers. As we start building out the  store, we'll create additional components that will be container  components to get data from the store and pass it to the presentational  components that need the data.

Thus far, we haven't done anything that's special to Redux; all of  the steps above are applicable and useful for React applications that do not use Redux. 

Remember that Redux doesn't care about *how* our app looks or what components it uses. Instead, it gives a way to manage the *state* of the application in a predictable way. When we talk about *state*, we're really talking about *data* - not just any kind of data inside the app, but data that can change based on the events in the app. 

Let's move on to Step 3, where we'll start thinking about the data in this app.