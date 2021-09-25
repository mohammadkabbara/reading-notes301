
# Converting a Function to a Class

You can convert a function component like Clock to a class in five steps:

Create an ES6 class, with the same name, that extends React.Component.

Add a single empty method to it called render().

Move the body of the function into the render() method.

Replace props with this.props in the render() body.

Delete the remaining empty function declaration.


<!-- <img src ="https://miro.medium.com/proxy/1*YgtCXuRGmPfPg2PogXVCfQ.png"/> -->

# Using State Correctly

There are three things you should know about setState().

**Do Not Modify State Directly**

**State Updates May Be Asynchronous**

**State Updates are Merged**

# The Data Flows Down

Neither parent nor child components can know if a certain component is stateful or stateless, and they shouldn’t care whether it is defined as a function or a class.

This is why state is often called local or encapsulated. It is not accessible to any component other than the one that owns and sets it.

# Handling Events

Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:

*React events are named using camelCase, rather than lowercase.*

*With JSX you pass a function as the event handler, rather than a string.*

# Use cases


Assuming your counter is important to your app, and is storing data that would be useful to other components, you would not want to use local state to keep this value.

The current best practice is to use local state to handle the state of your user interface (UI) state rather than data. For example, using a controlled component to fill out a form is a perfectly valid use of local state.

Another example of UI data that you could store in local state would be the currently selected tab from a list of options.

A good way to think about when to use local state is to consider whether the value you’re storing will be used by another component. If a value is specific to only a single component (or perhaps a single child of that component), then it’s safe to keep that value in local state.

Takeaway: keep UI state and transitory data (such as form inputs) in local state.

(from :https://www.freecodecamp.org/news/where-do-i-belong-a-guide-to-saving-react-component-data-in-state-store-static-and-this-c49b335e2a00/)

# How to force a React component to re-render

**React components** automatically re-render whenever there is a change in their state or props. A simple update of the state, from anywhere in the code, causes all the User Interface (UI) elements to be re-rendered automatically.

However, there may be cases where the render() method depends on some other data. After the initial mounting of components, a re-render will occur when:

**A component’s setState() method is called.**

**A component’s forceUpdate() method is called.**

(from :https://www.educative.io/edpresso/how-to-force-a-react-component-to-re-render)





