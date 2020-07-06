---
title: Setting Up Redux Without Pulling Your Hair Out 💆🏻‍♀️💓
published: false
series: React/Redux
---

## What is Redux?
Redux is a global state management tool used in JavaScript applications. It's most commonly used in React apps, but can also be paired with other libraries like Angular, Vue, and Mithril, just to name a few.

## What are the benefits of using Redux?
1. Global state management
If you've ever built a React app, you know how confusing [inverse data flow](https://dev.to) can be. While Redux doesn't completely erase the need for inverse data flow or local state management, it can make your life easier.

If you're building a complex app with several components, passing down props between many layers of components can become messy. Global state allows us to manage state indepently of our components and sits above our App component. Any component can access the global state without getting props passed down from its parent component. 

#### What is global state vs. local state?
Global state is independent of all other components. Its placed above the App component, usually in `index.js`.

2. Single source of truth
3. Code organization

## What are the downsides of implementing Redux?
1. Read-only
2. Overkill for simple apps

## How to set up Redux with a React App

## Maintaining your global state