---
title: Setting Up Redux Without Pulling Your Hair Out 💆🏻‍♀️💓
published: false
---

## What is Redux?
Redux is a global state management tool used in JavaScript applications. It's most commonly used in React apps, but can also be paired with other libraries like Angular, Vue, and Mithril, just to name a few.

## What are the benefits of using Redux?
If you've ever built a React app, you know how confusing inverse data flow can be. In React, only parent components and child components can communicate with each other. This means that components that are cousins or siblings cannot directly talk to each other.

#### What does this look like in code?
Let's say we're building an app that lets users create accounts with their email addresses. 

```javascript
class App extends React.Component {
  state = {
    email_address: ""
  }

  handleChange = (event) => {
    this.setState({
      email_address: event.target.value
    })
  }

  handleSubmit = (event) => {
    event.preventDefault()
    console.log("You successfully created an account!")
  }

  render () {
    return (
      <CreateAccountForm
        handleChange={this.handleChange}
        handleSubmit={this.handleSubmit}/>
      <AccountSettings />
    )
  }
}

class CreateAccountForm extends React.Component {
  render () {
    return (
      <div>
        <form onSubmit={this.props.handleSubmit}>
          <label>Email Address: </label>
          <input type="text" name="email_address" onChange={this.props.handleChange} />
          <input type="submit" value="Create Account"  />
        </form>
      </div>
    )
  }
}
```

## Local State vs. Global State

Global state is independent of all other components. Its placed above the App component.
Pure functions
Single source of truth
Read-only


## How to set up Redux with a React App

## Maintaining your global state