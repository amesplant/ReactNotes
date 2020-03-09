### 1. React Router Intro

<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/PV6TN8ahSX0?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=83" id="widget84" width="640" height="360" frameborder="0"></iframe>



## Single-Page Apps

Single-page applications can work in different ways. One way a single-page app loads is by downloading *the entire* site's contents all at once. This way, when you're navigating around on the site, everything is already available to the browser, and it  doesn't need to refresh the page. Another way single-page apps work is  by downloading everything that's needed to render the page the user  requested. Then when the user navigates to a new page, asynchronous  JavaScript requests are made for *just* the content that was requested. 

Another key factor in a good single-page app is that the URL controls the page content. Single-page applications are highly interactive, and  users want to be able to get back to a certain state using just the URL. Why is this important? Bookmarkability! (pretty sure that's not a  word...yet) When you bookmark a site, that bookmark is *only* a URL, it doesn't record the state of that page.

Have you noticed that any of the actions you perform in the app do  not update the page's URL? We need to create React applications that  offer bookmarkable pages!



## React Router

React Router turns React projects into single-page applications. It  does this by providing a number of specialized components that manage  the creation of links, manage the app's URL, provide transitions when  navigating between different URL locations, and so much more. 

According to the React Router website:

> React Router is a collection of **navigational components** that compose declaratively with your application. 

If you're interested, feel free to check out the website at https://reacttraining.com/.

In the next section, we'll dynamically render content to the page based on a value in the project's `this.state` object. We'll use this basic example as an idea of how React Router  works by controlling what's being seen via state. Then we'll switch over to using React Router. We'll walk you through installing React Router,  adding it to the project, and hooking everything together so it can  manage your links and URLs.