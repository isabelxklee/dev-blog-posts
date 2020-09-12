---
title: Launching Winner Winner, Chicken Dinner! 🐔⚡️
published: false
tags: react, javascript, html, css
# cover_image: https://i.imgur.com/KcLnrnU.png
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
* I'm not a huge fan of using Regex, so it was a bit of a pain to format the user's input into an array and then back into a string. I'm still figuring out the best way to deal with edge cases -- like, what do I do if the user doesn't follow my instructions on how to enter their list? What if they use line breaks instead of commas to separate their list items?

* I initially used Redux for global state management and stored the backend data in a `db.json` file. I quickly gave up on this idea when I realized that it would be overkill. Instead, I ended up refactoring my app to get and set the user's data with localStorage!

* I also wanted to avoid implementing authentication -- it seemed more accessible to allow the users to quickly create a list and play around with it, rather than forcing them to sign up before they could access any of the features. With the freedom of not needing to build auth, I started to brainstorm how I could structure the app without a backend API.

## The story behind Winner Winner
As a software engineering coach at Flatiron School, I lead several meetings a week where I have to pick on students to participate. We usually do a popcorn-style rotation where the person who just participated picks the next person to go. But with 25 students and 4 instructors in the class, it can be tedious taking account of who's already gone and who's still left.

One of my goals this year is to become a stronger frontend developer and become more familiar with JavaScript frameworks. I love working with React and Redux, so I decided to give myself a short deadline of building a single-page app using React and [styled components](https://styled-components.com).

## What would I do differently next time?
* Would've picked an easier dataset to work with if I knew how tricky it was going to be to load +7,000 data points (lol!)
* Would've done more research on different React tools for the Mapbox API before committing to the first one that I found and constantly refactoring my code
* Would've reached out for help earlier from my colleagues!

![Screenshot of the "spin the wheel" page for the Winner Winner, Chicken Dinner! app](https://i.imgur.com/gLXPs9x.png)

## Conclusion
Thanks for stopping by, and please make sure to check out [Winner Winner, Chicken Dinner](https://winnerwinnerapp.com)! It's also on [Product Hunt](https://www.producthunt.com/posts/winner-winner-chicken-dinner) if you want to give it an upvote. 💓