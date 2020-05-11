# 5. Step by Step Guide - React Apps



# *Step by Step Guide for Building React Apps*

## Planning Stage  📐

### Step 1 - Draw All of the Views of the App

We need to determine the look and functionality of each view in your  app. One of the best approaches is to draw each view of the app on paper so that you'll have a good idea of what information and data you're  planning to have on each page.

Instead of paper and pencil, you can be a bit more digital and use [software for creating mockups](https://codingsans.com/blog/mockup-tools). If you were given project specifications, check your mock against them  to make sure that you have all of the required features. 

### Step 2 - Break Each View Into a Hierarchy of Components

For this step,

- draw boxes around every component; and
- arrange our components into a hierarchy

### Step 3 - Determine the Data Each Component Needs

For each component, determine which data is the component accessing, getting, modifying, or showing.

### Step 4  - Determine Which Component Each Piece of Data Should Live in

If multiple components need the same data, store the data in the  components' closest common ancestor. Take a look at these example to see how that's done: [Lifting State Up](https://reactjs.org/docs/lifting-state-up.html) and [Thinking in React](https://reactjs.org/docs/thinking-in-react.html).

### Coding Stage🔨

**Step 1**- Create components that hold data.

**Step 2** - Create components that need data.

**Step 3** - Pass data from components that have it to components that need it.

**Step 4** - Debug and make sure that everything works as expected.

**Step 5** - Add inverse data flow (if you're confused about what that means, take a look at [this](https://reactjs.org/docs/thinking-in-react.html).

**Step 6** - Add navigation (We'll cover this topic next week - don't worry about it for now).

**Step 7** - Add finishing touches and make sure the project meets the [rubric](https://review.udacity.com/#!/rubrics/918/view).

Remember, this is just a template. As you build more projects, you'll modify this template to suit your needs. You may also find it more  intuitive to use a different approach. Regardless of the approach you  take, however, **planning out your app is imperative to success**. 