### 6. Finishing the Contact Form

## Create The Contact Form

Right now, the page to create contacts is empty! Let's build out a form on that page so we start adding our own custom contacts.

> ## ⚠️ Required File ⚠️

> At the beginning of the program, we gave you the option to clone our starter project or to start from scratch using [create-react-app](https://github.com/facebookincubator/create-react-app). If you haven't added it yet, you'll need [the ImageInput.js file](https://github.com/udacity/reactnd-contacts-complete/blob/master/src/ImageInput.js) for the following video.



The ImageInput component is a custom `` that dynamically reads and resizes image files before submitting them  to the server as data URLs. It also shows a preview of the image. We  chose to give this component to you rather than build it ourselves  because it contains features related to files and images on the web that aren't crucial to your education in this context. If you're curious,  feel free to dive into the code, but know it's not a requirement.



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/p3v2dgrqJsg?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=71" id="widget72" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/4b1693fa9b8268af8f1eb190d0bae66bf850ffb4)



## Serialize The Form Data

At this point, our form will serialize the values from user input (i.e., the `name` and `email`), adding them as a query string to the URL. We can add some additional  functionality by having our app serialize these form fields on its own.  After all, we want the app to ultimately handle creating the contact and saving it to the state. 

To accomplish this, we'll use the [form-serialize](https://www.npmjs.com/package/form-serialize) package to output this information as a regular JavaScript object for the app to use.

```bash
npm install --save form-serialize
```

Let's see it all in action!



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/aAhaXlQ2G6I?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=73" id="widget74" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/69c8b52ff523071db4ed9c5edb07aa34445d1570)



## Update Server With New Contact

We have our contact form. We're serializing our data and passing it  up to the parent component. All we need to do to have a fully functional app is to save the contact to the server.



<iframe class="embed-responsive-item" allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/24lu6iVQHro?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=75" id="widget76" width="640" height="360" frameborder="0"></iframe>



[Here's the commit with the changes made in this video.](https://github.com/udacity/reactnd-contacts-app/commit/f876f2d17b338e57ec80e8f67abbb3efa83bff2a)