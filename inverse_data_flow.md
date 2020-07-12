---
title: Understanding Inverse Data Flow in React 💃🏻
published: true
series: Intro to React/Redux
cover_image: https://i.imgur.com/WXFTo3A.png
---

## What is inverse data flow?
In React, inverse data flow allows us to send data between parent and child components as props, or properties. However, components that are cousins or siblings cannot directly communicate with each other.

## Sharing data between parent and child components
Here's an example of inverse data flow between a parent component and a child component. Let's say we're building an app that allows users to create accounts by entering their email addresses.

```javascript
class Home extends React.Component {
  state = {
    email_address: ""
  }

  handleChange = (inputFromChild) => {
    this.setState({
      email_address: inputFromChild
    })
  }

  handleResponse = (event) => {
    event.preventDefault()
    console.log("Something has been done.")
  }

  render () {
    return (
      <CreateAccountForm
        handleChange={this.handleChange}
        handleResponse={this.handleResponse}/>

      <AccountSettings
        handleChange={this.handleChange}
        handleResponse={this.handleResponse}/>
    )
  }
}
```

In our Home component, we're defining the `handleChange()` and `handleResponse()` functions and then sending them down as props to its child components, CreateAccountForm and AccountSettings. The information inputted by the user in these child components is then sent back up to the parent component by invoking those very same functions. This allows us to "reuse" these functions without having to copy and paste the same code in both of the child components.

If we didn't use props, here's what our components might look like:

```javascript
class Home extends React.Component {
  state = {
    email_address: ""
  }

  render () {
    return (
      <CreateAccountForm />
      <AccountSettings />
    )
  }
}

class CreateAccountForm extends React.Component {
  handleChange = (inputFromChild) => {
    this.setState({
      email_address: inputFromChild
    })
  }

  handleResponse = (event) => {
    event.preventDefault()
    console.log("Something has been done.")
  }

  render () {
    return (
      <div>
        <form onSubmit={this.handleResponse}>
          <label>Email Address: </label>
          <input type="text" name="email_address" onChange={this.handleChange} />
          <input type="submit" value="Create Account" />
        </form>

      </div>
    )
  }
}

class AccountSettings extends React.Component {
  handleChange = (inputFromChild) => {
    this.setState({
      email_address: inputFromChild
    })
  }

  handleResponse = (event) => {
    event.preventDefault()
    console.log("Something has been done.")
  }

  render () {
    return (
      <div>
        <form onSubmit={this.handleResponse}>
          <label>Email Address: </label>
          <input type="text" name="email_address" onChange={this.handleChange} />
          <input type="submit" value="Create Account" />
        </form>

      </div>
    )
  }
}
```

This isn't very DRY, is it? It also makes things complicated if we want to update the `handleChange()` and `handleReponse()` functions in both places. Placing those two functions in the Home component and sending it down to its child components creates a single source of truth.

## Limitations of inverse data flow
While inverse data flow is great for writing DRYer code, it can sometimes be too restrictive. For example, components that do not have a direct parent or child relationship cannot share props with each other.

![Graphic of inverse data flow relationships](https://i.imgur.com/GUuOmwI.png)

If we wrote a function called `toggleFormVisibility()` in our CreateAccountForm component, and we wanted to use it in our AccountSettings component, it would be not be available as a prop. In order to create access to that function, we would have to send it back up to the parent and back down to AccountSettings.

```javascript
class CreateAccountForm extends React.Component {
  state = {
    displayForm: false
  }

  toggleFormVisibility = () => {
    this.setState({
      displayForm: !this.state.displayform
    })
  }

  render () {
    return (
      <div>
        <button onClick={this.toggleFormVisibility}>Show the form</button>

        <form onSubmit={this.props.handleResponse}>
          <label>Email Address: </label>
          <input type="text" name="email_address" onChange={this.props.handleChange} />
          <input type="submit" value="Create Account" />
        </form>

      </div>
    )
  }
}
```

This process of sharing data can become quite cumbersome and confusing to follow if there are several components with complex relationships.

## Summary
1) Define the function in the parent component.

```javascript
class Home extends React.Component {
  state = {
    email_address: ""
  }

  handleChange = (inputFromChild) => {
    this.setState({
      email_address: inputFromChild
    })
  }

  render () {
    return (
      <CreateAccountForm />
      <AccountSettings />
    )
  }
}
```

2) Send down the function as props to the child component.

```javascript
class Home extends React.Component {
  ...

  render () {
    return (
      <CreateAccountForm handleChange={this.handleChange} />
      <AccountSettings handleChange={this.handleChange} />
    )
  }
}
```

3) Invoke the function in the child.
4) Send data back up to the parent as props.

```javascript
class CreateAccountForm extends React.Component {
  render () {
    return (
      <div>
        <form>
          <label>Email Address: </label>
          <input type="text" name="email_address" onChange={this.props.handleChange} />
          <input type="submit" value="Create Account" />
        </form>

      </div>
    )
  }
}
```

5) Voila! You've just created inverse data flow.