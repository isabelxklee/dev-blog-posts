---
title: Understanding Inverse Data Flow in React
published: false
---

#### What is Inverse Data Flow?
In React, inverse data flow allows us to send data between parent and child components as props, or properties. However, components that are cousins or siblings cannot directly communicate with each other.

#### Example Scenario
Here's an example of inverse data flow between a parent component and a child component. Let's say we're building an app that allows users to create accounts by entering their email addresses.

From our `App` component, we can send the `handleChange` and `handleSubmit` functions down to the `CreateAccountForm` component as props. This allows us to "reuse" these functions for other components, like the `AccountSettings` component by also sending them down as props.

If the `handleChange` function – which is used in both `CreateAccountForm` and `AccountSettings` – were housed in either of the child components, it wouldn't be accessible to each other. We would have to copy and paste the function into the other sibling component (which is not very DRY!), or we'd have to send it back up to the parent component and then back down to the other sibling (which would not be as intuitive from a code organization standpoint).

```javascript
class App extends React.Component {
  state = {
    email_address: ""
  }

  handleChange = (inputFromChild) => {
    this.setState({
      email_address: inputFromChild
    })
  }

  handleSubmit = (event) => {
    event.preventDefault()
    console.log("You've successfully created an account!")
  }

  handleUpdate = (event) => {
    event.preventDefault()
    console.log("Your email address has been updated.")
  }

  render () {
    return (
      <CreateAccountForm
        handleChange={this.handleChange}
        handleSubmit={this.handleSubmit}/>

      <AccountSettings
        handleChange={this.handleChange}
        handleUpdate={this.handleUpdate}/>
    )
  }
}

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

        <form onSubmit={this.props.handleSubmit}>
          <label>Email Address: </label>
          <input type="text" name="email_address" onChange={this.props.handleChange} />
          <input type="submit" value="Create Account" />
        </form>

      </div>
    )
  }
}
```