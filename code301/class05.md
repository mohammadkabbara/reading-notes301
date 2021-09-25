**React is, in our opinion, the premier way to build big, fast Web apps with JavaScript. It has scaled very well for us at Facebook and Instagram.**

# Break The UI Into A Component Hierarchy

*The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names.*


**But how do you know what should be its own component?** Use the same techniques for deciding if you should create a new function or object. One such technique is the *single responsibility principle,* that is, a component should ideally only do one thing. If it ends up growing, it should be decomposed into smaller subcomponents.


Since you’re often displaying a JSON data model to a user, you’ll find that if your model was built correctly, your UI (and therefore your component structure) will map nicely. That’s because UI and data models tend to adhere to the same information architecture. Separate your UI into components, where each component matches one piece of your data model.

# Build A Static Version in React

Now that you have your component hierarchy, it’s time to implement your app. The easiest way is to build a version that takes your data model and renders the UI but has no interactivity. It’s best to decouple these processes because building a static version requires a lot of typing and no thinking, and adding interactivity requires a lot of thinking and not a lot of typing. We’ll see why.

**To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props.**


# Identify The Minimal (but complete) Representation Of UI State

To make your UI interactive, you need to be able to trigger changes to your underlying data model. React achieves this with state.

*To build your app correctly, you first need to think of the minimal set of mutable state that your app needs. The key here is DRY: Don’t Repeat Yourself. Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand. For example, if you’re building a TODO list, keep an array of the TODO items around; don’t keep a separate state variable for the count. Instead, when you want to render the TODO count, take the length of the TODO items array.*

# Add Inverse Data Flow
React makes this data flow explicit to help you understand how your program works, but it does require a little more typing than traditional two-way data binding.