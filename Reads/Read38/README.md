# Conditional Rendering
onditional rendering in React works the same way conditions work in JavaScript.

While declaring a variable and using an if statement is a fine way to conditionally render a component, sometimes you might want to use a shorter syntax.

Inline If with Logical && Operator You may embed expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical && operator. It can be handy for conditionally including an element:

```
function Mailbox(props) {
  const unreadMessages = props.unreadMessages;
  return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
}

const messages = ['React', 'Re: React', 'Re:Re: React'];
ReactDOM.render(
  <Mailbox unreadMessages={messages} />,
  document.getElementById('root')
);
```
Inline If-Else with Conditional Operator Another method for conditionally rendering elements inline is to use the JavaScript conditional operator condition ? true : false.

Preventing Component from Rendering In rare cases you might want a component to hide itself even though it was rendered by another component. To do this return null instead of its render output.

# Basic List Component
Usually you would render lists inside a component.

We can refactor the previous example into a component that accepts an array of numbers and outputs a list of elements.

# Keys
Keys help React identify which items have changed, are added, or are removed. Keys should be given to the elements inside the array to give the elements a stable

The best way to pick a key is to use a string that uniquely identifies a list item among its siblings. Most often you would use IDs from your data as keys:

```
const todoItems = todos.map((todo) =>
  <li key={todo.id}>
    {todo.text}
  </li>
);
```
Keys Must Only Be Unique Among Siblings Keys used within arrays should be unique among their siblings. However, they don’t need to be globally unique.

Embedding map() in JSX

```
function NumberList(props) {
  const numbers = props.numbers;
  const listItems = numbers.map((number) =>
    <ListItem key={number.toString()}
              value={number} />
  );
  return (
    <ul>
      {listItems}
    </ul>
  );
}
```
# Forms
Since the value attribute is set on our form element, the displayed value will always be this.state.value, making the React state the source of truth. Since handleChange runs on every keystroke to update the React state, the displayed value will update as the user types.

```
class NameForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {value: ''};

    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }

  handleChange(event) {
    this.setState({value: event.target.value});
  }

  handleSubmit(event) {
    alert('A name was submitted: ' + this.state.value);
    event.preventDefault();
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <label>
          Name:
          <input type="text" value={this.state.value} onChange={this.handleChange} />
        </label>
        <input type="submit" value="Submit" />
      </form>
    );
  }
}
```
Notice that this.state.value is initialized in the constructor, so that the text area starts off with some text in it.

The file input Tag In HTML, an lets the user choose one or more files from their device storage to be uploaded to a server or manipulated by JavaScript via the File API.

```<input type="file" />```

# Handling Multiple Inputs
When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of

```event.target.name```

# Controlled Input Null Value
Specifying the value prop on a controlled component prevents the user from changing the input unless you desire so. If you’ve specified a value but the input is still editable, you may have accidentally set value to undefined or null.

# Alternatives to Controlled Components
It can sometimes be tedious to use controlled components, because you need to write an event handler for every way your data can change and pipe all of the input state through a React component. This can become particularly annoying when you are converting a preexisting codebase to React, or integrating a React application with a non-React library. In these situations, you might want to check out uncontrolled components, an alternative technique for implementing input forms.

# Composition vs Inheritance
## Containment
Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”.

Anything inside the JSX tag gets passed into the FancyBorder component as a children prop. Since FancyBorder renders {props.children} inside a

, the passed elements appear in the final output.
Sometimes we think about components as being “special cases” of other components. For example, we might say that a WelcomeDialog is a special case of Dialog.

# So What About Inheritance
Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that components may accept arbitrary props, including primitive values, React elements, or functions.

If you want to reuse non-UI functionality between components, we suggest extracting it into a separate JavaScript module. The components may import it and use that function, object, or a class, without extending it.

# Thinking in React
Start With A Mock
Imagine that we already have a JSON API and a mock from our designer.

- Step 1: Break The UI Into A Component Hierarchy
The first thing you’ll want to do is to draw boxes around every component (and subcomponent) in the mock and give them all names. If you’re working with a designer, they may have already done this, so go talk to them! Their Photoshop layer names may end up being the names of your React components!

1-FilterableProductTable (orange): contains the entirety of the example 2-SearchBar (blue): receives all user input 3- ProductTable (green): displays and filters the data collection based on user input 4- ProductCategoryRow (turquoise): displays a heading for each category 5-ProductRow (red): displays a row for each product

- Step 2: Build A Static Version in React

To build a static version of your app that renders your data model, you’ll want to build components that reuse other components and pass data using props. props are a way of passing data from parent to child. If you’re familiar with the concept of state, don’t use state at all to build this static version. State is reserved only for interactivity, that is, data that changes over time. Since this is a static version of the app, you don’t need it.

You can build top-down or bottom-up. That is, you can either start with building the components higher up in the hierarchy (i.e. starting with FilterableProductTable) or with the ones lower in it (ProductRow). In simpler examples, it’s usually easier to go top-down, and on larger projects, it’s easier to go bottom-up and write tests as you build.

- Step 3: Identify The Minimal (but complete) Representation Of UI State
Think of all the pieces of data in our example application. We have: To build your app correctly, you first need to think of the minimal set of mutable state that your app needs. The key here is DRY: Don’t Repeat Yourself. Figure out the absolute minimal representation of the state your application needs and compute everything else you need on-demand. For example, if you’re building a TODO list, keep an array of the TODO items around; don’t keep a separate state variable for the count. Instead, when you want to render the TODO count, take the length of the TODO items array.

- The original list of products

- The search text the user has entered

- The value of the checkbox

- The filtered list of products

- Identify Where Your State Should Live

For each piece of state in your application:

Identify every component that renders something based on that state. Find a common owner component (a single component above all the components that need the state in the hierarchy). Either the common owner or another component higher up in the hierarchy should own the state. If you can’t find a component where it makes sense to own the state, create a new component solely for holding the state and add it somewhere in the hierarchy above the common owner component.

Let’s run through this strategy for our application:

ProductTable needs to filter the product list based on state and SearchBar needs to display the search text and checked state. The common owner component is FilterableProductTable. It conceptually makes sense for the filter text and checked value to live in FilterableProductTable Cool, so we’ve decided that our state lives in FilterableProductTable. First, add an instance

- Step 5: Add Inverse Data Flow
React makes this data flow explicit to help you understand how your program works, but it does require a little more typing than traditional two-way data binding.

If you try to type or check the box in the previous version of the example (step 4), you’ll see that React ignores your input. This is intentional, as we’ve set the value prop of the input to always be equal to the state passed in from FilterableProductTable.