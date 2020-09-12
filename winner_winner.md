---
title: Launching Winner Winner, Chicken Dinner! 🐔⚡️
published: true
tags: react, css, showdev, webdev
cover_image: https://i.imgur.com/GB5LVVY.png
---

## App launch
Last week, I launched a random name picker app called [Winner Winner, Chicken Dinner!](https://www.winnerwinnerapp.com) It's a lightweight React app where you can create a list of names or objects, and spin the wheel to display a random item each time.

![Screenshots of the Winner Winner, Chicken Dinner! app](https://camo.githubusercontent.com/79201cfeb0023d9223e87186ad2776db7a013f04/68747470733a2f2f692e696d6775722e636f6d2f7356724d3431532e706e67)

## How does it work?
* You can create a new list with the ability to edit it and delete it.
* Every time you spin the wheel, the app will choose a random item to display.
* Once you've gone through your whole list, you can go back to your list.
* As long as you don't clear your browser cookies, you can always access your most recent list!

## Some programming quirks
#### Feeling the pain of regex
I'm not a huge fan of using regex (which stands for "regular expression"), so it was a bit of a pain to format the user's input into an array and then back into a string. I'm still figuring out the best way to deal with edge cases – like, what do I do if the user doesn't follow my instructions on how to enter their list? What if they use line breaks instead of commas to separate their list items?

```javascript
  // regex logic for turning the user's input into an array
  formatStringToArr = (string) => { 
    return string.replace( /[\r\n]+/gm, ", " ).split(", ")
  }

  // taking the new array, randomizing the order by using the chance dependency, and then turning into a string again to save it to localStorage
  formatLocalStorage = () => {
  let peopleArray = this.formatStringToArr(localStorage.people)
  peopleArray = chance.shuffle(peopleArray)
  localStorage.setItem("people", peopleArray.join(", "))

  this.setState({
    array: peopleArray
  })
}
```

#### State management
I initially used Redux for global state management and stored the backend data in a `db.json` file. I quickly gave up on this idea when I realized that it would be overkill. Instead, I ended up refactoring my app to get and set the user's data with localStorage!

```javascript
  // saving the user's input to the local state
  handleChange = (event) => {
    this.setState({
      [event.target.name]: event.target.value
    })
  }

  // saving the local state to localStorage and then redirecting the user to their new list page!
  handleSubmit = (event) => {
    event.preventDefault()
    localStorage.setItem("title", this.state.title)
    localStorage.setItem("people", this.state.people)
    this.props.history.push("/list")
  }
```

#### To auth or not to auth?
I also wanted to avoid implementing authentication – it seemed more accessible to allow the users to quickly create a list and play around with it, rather than forcing them to sign up before they could access any of the features. With the freedom of not needing to build auth, I started to brainstorm how I could structure the app without a backend API.

## The story behind Winner Winner
As a software engineering coach at [Flatiron School](https://flatironschool.com), I lead several meetings a week where I have to pick on students to participate. We usually do a popcorn-style rotation where the person who just participated picks the next person to go. But with 25 students and 4 instructors in the class, it can be tedious taking account of who's already gone and who's still left.

I took this as a chance to create a fun, light tool that would be useful for teachers, managers, and anyone else who needs a randomized list!

One of my goals this year is also to become a stronger frontend developer and familiarize myself more with different JavaScript frameworks. I love working with React, so I decided to give myself the goal of creating this app within a couple weeks. Winner Winner, Chicken Dinner! is built using React and [styled components](https://styled-components.com).

![Winner Winner, Chicken Dinner! logo](https://i.imgur.com/GB5LVVY.png)

## Conclusion
Thanks for stopping by, and please make sure to check out [Winner Winner, Chicken Dinner](https://winnerwinnerapp.com)! It's also on [Product Hunt](https://www.producthunt.com/posts/winner-winner-chicken-dinner) if you want to give it an upvote. 💓