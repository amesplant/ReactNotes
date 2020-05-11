# 1. Project Details



<iframe allowfullscreen="1" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" title="YouTube video player" src="https://www.youtube.com/embed/fa1yhSA90-w?showinfo=0&amp;rel=0&amp;autohide=1&amp;vq=hd720&amp;hl=en-us&amp;cc_load_policy=0&amp;enablejsapi=1&amp;origin=https%3A%2F%2Fclassroom.udacity.com&amp;widgetid=455" id="widget456" width="640" height="360" frameborder="0"></iframe>



# Project Overview

For the **UdaciCards** project, you will build a mobile  application (Android or iOS - or both) that allows users to study  collections of flashcards. The app will allow users to create different  categories of flashcards called "decks", add flashcards to those decks,  then take quizzes on those decks.

## Why this project?

This project encompasses the fundamental aspects of building a native application including handling infinite lists, routing, and user input. By building this project, you will gain an understanding of how to use  React Native to build an iOS and Android application.

# Specification

You'll create your project using **create-react-native-app**. There will be no starter code that you need to download. 

The specification provided in this [rubric](https://review.udacity.com/#!/rubrics/1021/view) is the minimum required for this project. You may extend your project however you'd like.

## Specific Requirements

- Use create-react-native-app to build your project.
- Allow users to create a deck which can hold an unlimited number of cards.
- Allow users to add a card to a specific deck. 
- The front of the card should display the question.
- The back of the card should display the answer.
- Users should be able to quiz themselves on a specific deck and receive a score once they're done. 
- Users should receive a notification to remind themselves to study if they haven't already for that day.

## Views

Your application should have, at a minimum, five views.

- Deck List View (Default View)
  - displays the title of each Deck
  - displays the number of cards in each deck



[![Deck List View](https://video.udacity-data.com/topher/2017/September/59c19a6a_20170919-151343/20170919-151343.png)Deck List View ](https://classroom.udacity.com/nanodegrees/nd019/parts/9b15c3b4-c38a-4fcd-8fe7-47937b293a3a/modules/ac68e92f-8a1a-4b6f-8af6-86169d024d26/lessons/49853866-e353-4a5f-86c2-21beeac1dfe8/concepts/4a0c5448-4b5d-4f30-8db3-e7aaf0295701#)



- Individual Deck View
  - displays the title of the Deck
  - displays the number of cards in the deck
  - displays an option to start a quiz on this specific deck
  - An option to add a new question to the deck



[![Individual Deck View](https://video.udacity-data.com/topher/2017/September/59c19b96_20170919-153231/20170919-153231.png)Individual Deck View ](https://classroom.udacity.com/nanodegrees/nd019/parts/9b15c3b4-c38a-4fcd-8fe7-47937b293a3a/modules/ac68e92f-8a1a-4b6f-8af6-86169d024d26/lessons/49853866-e353-4a5f-86c2-21beeac1dfe8/concepts/4a0c5448-4b5d-4f30-8db3-e7aaf0295701#)



- Quiz View
  - displays a card question
  - an option to view the answer (flips the card)
  - a "Correct" button
  - an "Incorrect" button
  - the number of cards left in the quiz
  - Displays the percentage correct once the quiz is complete



[![Quiz View](https://video.udacity-data.com/topher/2017/September/59c19ca8_20170919-151227/20170919-151227.png)Quiz View ](https://classroom.udacity.com/nanodegrees/nd019/parts/9b15c3b4-c38a-4fcd-8fe7-47937b293a3a/modules/ac68e92f-8a1a-4b6f-8af6-86169d024d26/lessons/49853866-e353-4a5f-86c2-21beeac1dfe8/concepts/4a0c5448-4b5d-4f30-8db3-e7aaf0295701#)



[![img](https://video.udacity-data.com/topher/2017/September/59c19d22_20170919-151123/20170919-151123.png)](https://classroom.udacity.com/nanodegrees/nd019/parts/9b15c3b4-c38a-4fcd-8fe7-47937b293a3a/modules/ac68e92f-8a1a-4b6f-8af6-86169d024d26/lessons/49853866-e353-4a5f-86c2-21beeac1dfe8/concepts/4a0c5448-4b5d-4f30-8db3-e7aaf0295701#)



- New Deck View
  - An option to enter in the title for the new deck
  - An option to submit the new deck title



[![img](https://video.udacity-data.com/topher/2017/September/59c19f5a_20170919-151320/20170919-151320.png)](https://classroom.udacity.com/nanodegrees/nd019/parts/9b15c3b4-c38a-4fcd-8fe7-47937b293a3a/modules/ac68e92f-8a1a-4b6f-8af6-86169d024d26/lessons/49853866-e353-4a5f-86c2-21beeac1dfe8/concepts/4a0c5448-4b5d-4f30-8db3-e7aaf0295701#)



- New Question View
  - An option to enter in the question
  - An option to enter in the answer
  - An option to submit the new question



[![img](https://video.udacity-data.com/topher/2017/September/59c19f82_20170919-151259/20170919-151259.png)](https://classroom.udacity.com/nanodegrees/nd019/parts/9b15c3b4-c38a-4fcd-8fe7-47937b293a3a/modules/ac68e92f-8a1a-4b6f-8af6-86169d024d26/lessons/49853866-e353-4a5f-86c2-21beeac1dfe8/concepts/4a0c5448-4b5d-4f30-8db3-e7aaf0295701#)



## Data

We'll use `AsyncStorage` to store our decks and flashcards. Redux is optional for this project.

Using `AsyncStorage` you'll manage an object whose shape is similar to this:

```js
{
  React: {
    title: 'React',
    questions: [
      {
        question: 'What is React?',
        answer: 'A library for managing user interfaces'
      },
      {
        question: 'Where do you make Ajax requests in React?',
        answer: 'The componentDidMount lifecycle event'
      }
    ]
  },
  JavaScript: {
    title: 'JavaScript',
    questions: [
      {
        question: 'What is a closure?',
        answer: 'The combination of a function and the lexical environment within which that function was declared.'
      }
    ]
  }
}
```

Notice each deck creates a new key on the object. Each deck has a `title` and a `questions` key. `title` is the title for the specific deck and `questions` is an array of questions and answers for that deck. 

## Tip

> To manage your `AsyncStorage` database, you'll want to create four different helper methods.

> `getDecks`: return all of the decks along with their titles, questions, and answers. 
>  `getDeck`: take in a single `id` argument and return the deck associated with that id. 
>  `saveDeckTitle`: take in a single `title` argument and add it to the decks. 
>  `addCardToDeck`: take in two arguments, `title` and `card`, and will add the card to the list of questions for the deck with the associated title. 