# Component Based UI

## Review, Research, and Discussion
### 1. Name 5 Javascript UI Frameworks (other than React)
* Angular
* Vue
* Ember
* Svelte 3
*  Ext JS by Sencha

### 2. What’s the difference between a framework and a library?
The key difference between a library and a framework is **"Inversion of Control"**.
 
When you call a method from a library, you are in control. But with a framework, the control is inverted: the framework calls you.

![](https://csharpcorner-mindcrackerinc.netdna-ssl.com/UploadFile/a85b23/framework-vs-library/Images/DqCkT.png)


### Term
**Rendering :** refers to showing the output in the browser.

**Templates :** Templating refers to the client side data binding method implemented with the JavaScript language. Popular JavaScript templating languages are: AngularJS, Backbone.js, Ember.js, Handlebars.js, and Mustache.js. 

**State :** describes the status of the entire program or an individual object. It could be text, a number, a boolean, or another data type. It's a common tool for coordinating code. For example, once you update state, a bunch of different functions can instantly react to that change.


### Preparation Materials:

***React is a JavaScript library***

**Introducing JSX**

JSX is a syntax extension to JavaScript, it produces React "elements"

**Why JSX?**

  React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.

Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called **“components” that contain both**. 

**React doesn’t require using JSX,** but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

**Embedding Expressions in JSX**

*You can put any valid JavaScript expression inside the curly braces in JSX.* 


**JSX is an Expression Too**
After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.

**This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions**

**Specifying Attributes with JSX**
*You may use quotes to specify string literals as attributes*

*You may also use curly braces to embed a JavaScript expression in an attribute*

**JSX Prevents Injection Attacks**
It is safe to embed user input in JSX:
```js
const title = response.potentiallyMaliciousInput;
// This is safe:
const element = <h1>{title}</h1>;
```

**JSX Represents Objects**: 
Babel compiles JSX down to React.createElement() calls.

These objects are called “React elements”. You can think of them as descriptions of what you want to see on the screen. React reads these objects and uses them to construct the DOM and keep it up to date.



### Rendering Elements
Elements are the smallest building blocks of React apps.

An element describes what you want to see on the screen:

**Rendering an Element into the DOM**
```js
<div id="root"></div>
```
1. We call this a “root” DOM node because everything inside it will be managed by React DOM.
2. To render a React element into a root DOM node, pass both to **ReactDOM.render()**:
   
   ```js
   const element = <h1>Hello, world</h1>;
   ReactDOM.render(element, document.getElementById('root'));
   ```



**Updating the Rendered Element**
React elements are **immutable**. Once you create an element, **you can’t change its children or attributes.** An element is like a single frame in a movie: it represents the UI at a certain point in time.

With our knowledge so far, **the only way to update the UI is to create a new element, and pass it to ReactDOM.render().**
  ```js
function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);

  ```

**React Only Updates What’s Necessary**

React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.
