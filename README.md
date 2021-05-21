# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Intro to React.js


### Learning Objectives

*After this lesson, you will be able to:*

- Identify and define React components
- Describe why we use components in React
- Build a React component
- Describe JSX
- Describe the Virtual DOM versus the standard DOM
- Understand how components are called
- Describe props
- Create a component that renders props
- Pass multiple individual props to a component
- Pass multiple props as an object to a component

<br>


---

![react-logo](https://i.imgur.com/NFaSqiT.png)

---

Welcome! This lesson assumes you have some JavaScript knowledge and awareness of the DOM tree. Beyond that, we'll be here to teach you!     

## What is ReactJS?

- [React Homepage](https://reactjs.org/)

First, let's think about where you might see a React.js app. Here are two quick and easy examples:

- Facebook
  - Facebook actually built React! It needed web pages that could change quickly based on a user's interaction — your Facebook feed, for example.

- Instagram
  - Instagram's public feed and internal system are entirely built on React.

For an intro to React, watch [this video](https://generalassembly.wistia.com/medias/lr8idjxtx8) (note: right click to open in a new tab!).

The React framework was built to solve one problem: building large applications with data that changes over time.

Before React, re-rendering one thing meant re-rendering everything.
This had negative implications on processing power and ultimately user experience, which at times became glitchy and laggy.

React is "agnostic" to other tools in your front end. This means that React can co-exist with other Javascript frameworks, letting the other frameworks handle the models and controllers and having React sort out the views.


#### Some History

For a quick rundown, React was...
* First used by Facebook in 2011.
* Adopted by Instagram in 2012.
* Made open source in May 2013.

This can be extrapolated to - both Facebook and Instagram are React apps!

To get more hands on and in-depth down the React rabbit hole, let's keep going!


*If you want to get an in-depth taste of what React is all about, [here's an introduction from React.js Conf 2015](https://www.youtube.com/watch?v=KVZ-P-ZI6W4&feature=youtu.be&t=510). (note: right click to open in a new tab!). We'd recommend starting around the 8:35 mark and watching until 16:30. This link is also in the Further Reading page at the end of the React module.*

<br>

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Components and JSX


## Components

- [Completed Stack Blitz App](https://stackblitz.com/edit/react-ma62ih?)

The basic unit you'll be working with in ReactJS is a **component**. Components are pieces of our application that we can define once and reuse all over the place.

For an intro to components, watch [this video](https://generalassembly.wistia.com/medias/h64z7lp1ir) (note: right click to open in a new tab!).


If you're used to writing out all of a page's view in a single HTML file, using components is a very different way of approaching web development.

With components, there is more integration and less separation of HTML, CSS, and JavaScript.

- Instead of creating a few large files, you will organize your web app into small, reusable components that encompass their own content, presentation, and behavior.

When using React, building components will be your main front-end task.
- Because they're so encapsulated, components make it easy to reuse your code, test, and separate concerns.

### [F.I.R.S.T. Components](https://addyosmani.com/first/)

A React component is built to expect an input and render a UI with it. More importantly, a well-structured component only receives data specific to its purpose.

This is because React follows a more **functional** approach to programming. For React components under this approach, **the same input will always produce the same output**.

Best practice is that React components follow the **F.I.R.S.T.** guidelines

#### Focused

Components should do one thing and do it well.

#### Independent

Components should increase cohesion and reduce coupling. Behavior in one component should not impact the behavior of another. In other words, components should not rely on one another.

> But they should compliment one another.

#### Reusable

Components should be written in a way that reduces the duplication of code.

#### Small

Ideally, components should be short and condensed.

#### Testable

Because the same input will always produce the same output, components are easily unit testable.

> If you're interested, [Jest](https://facebook.github.io/jest/docs/tutorial-react.html) is a popular testing library for React.

### Identifying Components

Take a look at [CraigsList](https://boston.craigslist.org/search/aap) (note: right click to open in a new tab!).

![Components](https://i.imgur.com/bnazcML.png)

Each listing is a component. How can you identify this?
- Listings look identical in structure, but have different information populating them
- Listings are dynamically generated based on the user's search

<!--- Now, go to [Amtrak.com](https://www.amtrak.com/home) (note: right click to open in a new tab!). We want to look at the listing page, so put in any "From" (for example, New York - Penn Station), any "To" (for example, Boston - South Station), and pick any date. Hit "Find Trains". Now look at the listing page:

![Amtrak](images/amtrak.png) --->

Now, check out this website, Tube Tracker.

![tube tracker](https://i.imgur.com/59nCojL.png)

Scrolling down it, identify the visual "components" the website is comprised of. We suggest drawing this out on paper! So something like this...

![Component diagram](https://i.imgur.com/qpAuoxG.png)

As you're drawing this out, think about the following questions...

* Where do you see "nested components;" that is, where are there components inside another component? Where do you see just one "layer" instead?
* Are there any components that share the same structure?
* For components that share the same structure, what is different about them?


### So -

What does a component look like? Let's start with a simple "Hello World" example...

#### Code along: A Very Basic Component

In this section, we'll walk through:
* Removing the pre-filled contents of your `hello-world` app.
  - `create-react-app` filled your app with sample content - let's make room for your app!
* Adding your own component definition.
  - You want the app to display the words "Hello World!"
- Going through what we've done in detail!

To start, remove the entire contents of the `src/App.js` file.

Then, add the component definition below.

```js
import React from "react";
import "./style.css";

export default function App() {
  return (
    <div>
      <h1>Hello StackBlitz!</h1>
      <p>Start editing to see some magic happen :)</p>
    </div>
  );
}
```

Let's break down the things we see here...

##### `import React from 'react'`;
This imports React methods from the React library.

##### `function App()`

This is the functional component we're creating. In this example, we are creating a component and calling it "App."


##### `return()`

Every component has, at minimum, a `return` method. The `return` method is what renders the component to the screen, so it controls what is displayed for this component. From this function, we return what we want to display.  

- In our case, we are rendering a "Hello StackBlitz!" heading: `<h1>Hello StackBlitz!</h1>` and a `<p>Start editing to see some magic happen :)</p>`

> Note! That heading tag above looks like it's straight out of HTML, but it's actually a special language called JSX, which you'll see on the next page. For now, know that JSX will act like HTML when it's rendered to the screen.

##### `export default`

This exposes the `App` component to other files.  This means that other files can `import` from the `App.js` file in order to use the `App` component. In our case, we'll be importing it into `index.js` by calling an `import` to `App.js`.

When we try to import something from `App.js`, JavaScript will attempt to match a named export.

- Our only named export in `App.js` is `App`.

The `default` keyword means that if we try to import anything from this file that the app can't find, JavaScript will automatically revert to importing `App` instead.

- Only one default export is allowed per file.



### Wait - What's that HTML doing in my Javascript?

This is currently the contents of our `src/App.js` file:

```js
import React from "react";
import "./style.css";

export default function App() {
  return (
    <div>
      <h1>Hello StackBlitz!</h1>
      <p>Start editing to see some magic happen :)</p>
    </div>
  );
}
```

Let's talk about the value that the return method returns. It looks an awful lot like an HTML heading, but it's not. We often write out React components in **JSX**.

Wait, what's that? Try it yourself alongside [this video](https://generalassembly.wistia.com/medias/dcps4dqziy) in [this codepen](https://codepen.io/susir/pen/wJPoBw) (note: right click  both links to open in a new tab!)

So, JSX allows us to write code that strongly resembles HTML. It is eventually compiled to lightweight JavaScript objects.

Your `App` component's `return` method:

- Currently returns JSX, not HTML.
- The JSX creates a heading with `'Hello World!'`. and a `p` tag
- Your component reads this and renders a "Hello World!" heading andthe contents of the `p` tag.

> React can be written without JSX. We won't be doing this, but if you want to learn more, [check out this blog post](http://jamesknelson.com/learn-raw-react-no-jsx-flux-es6-webpack/) (note: open in new tab!).

### Challenge: Greet the day!

- Change your `App` component to return multiple lines.
  - Add a line below the "Hello StackBlitz!" heading that will display `"It is time for tea."` in an `h3`.

> Hint: Remember, the return statement can only return one DOM element. You can, however, place multiple elements within a parent `div` element.*
 
<br>

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) The Virtual DOM


### Review and Refactor

`App` in `src/App.js` is our component. It has a `return` method that returns the JSX for our "Hello StackBlitz!" and heading tags. Keeping components separate and organized is a best practice, so we created that function in its own file.

To show up on the page, though, that component still needs to actually be called from somewhere.  The main "hub" of our React app is `src/index.js`.  We'll investigate how `src/index.js` is currently loading and rendering the component, and we'll improve the code by making it more explicit and readable.

Look at your `src/index.js` file, and contrast it with the code below.


```js
import React from "react";
import ReactDOM from "react-dom";

import App from "./App";

ReactDOM.render(<App />, document.getElementById("root"));
```

>  This line imports the `App` component from the `src/App.js` file. Remember, the `default` part of `export default function App` in `src/App.js` means that importing other names - like `App` - actually _already_ brings in the `App` component! As a best practice, though, we're going to explicitly import the `App` component.


### Virtual DOM Intro

You should be familiar with the DOM.  You may have noticed that our `src/index.js` code mentions `ReactDOM`.  `ReactDOM` doesn't refer to the same DOM we know. Instead, it refers to a **Virtual DOM**. The Virtual DOM is a key piece of how React works.

So, how is different? Watch [this video](https://generalassembly.wistia.com/medias/v5qyqsir0s) to find out. _(note: right click for new tab!)_

In React, the virtual DOM is a staging area for changes that will eventually be implemented.

![Virtual DOM Diagram](https://docs.google.com/drawings/d/11ugBTwDkqn6p2n5Fkps1p3Elp8ZToIRzXzvM4LJMYaU/pub?w=543&h=229)

  > If you're interested in learning more about the Virtual DOM, [check this video out](https://www.youtube.com/watch?v=-DX3vJiqxm4). _(note: right click for new tab!)_

You know every component has, at a minimum, a `return` method. The `return` method generates a Virtual DOM node to be added to the actual DOM.

The contents of this node are what we define in the method's return statement, using JSX.

The `ReactDOM.render()` function takes two arguments:

```js
ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

- `<App />` uses **the name of the component to render**. In our `App.js` file, the `App` component returns the content to render:  a div with "Hello StackBlitz!" and heading tags (written in JSX). As a reminder, this is the `App` component:

```js
import React from "react";
import "./style.css";

export default function App() {
  return (
    <div>
      <h1>Hello StackBlitz!</h1>
      <p>Start editing to see some magic happen :)</p>
      <h3>It's time for tea</h3>
    </div>
  );
}
```

- The second argument of the `ReactDOM.render()` function is `document.getElementById('root')`; this finds **the DOM element to append that content to**. This argument can be any element on the page. Here, we're simply appending it to an element with the id `root`.  (Look through the `public/index.html` file if you're curious about the HTML structure.)

When our `index.js` is processed, React compares the virtual DOM to the regular DOM and only updates the `root` element on the page.


> Side note: What is `<App />` written in? JSX! Whenever you use a
self-closing tag in JSX, you **MUST** end it with a `/`, like `<App />` in the above example. If you don't use a self-closing tag, JSX will look for a closing tag and never find it!


<br>

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Props


## Component Data with Props

The React framework was built to handle data that changes over time.

So far, we have defined an `App` component in `App.js`. The component's `return` method returns a div with a few headings, written in JSX.

In `index.js`, we are importing this component, appending what the `App` component `render` method returns to the virtual DOM, and rendering that.

This is great, but it doesn't involve any data yet, let alone data that changes over time!   Let's make it more interesting.

Rather than simply display "Hello StackBlitz", let's display a greeting to the user. We'll make the greeting change dynamically based on the user's name.

The question is, how do we add a name to our `App` component without hardcoding it into the component's `return` method?

Find out! Try it yourself alongside [this video](https://generalassembly.wistia.com/medias/gchiu63slo) in [this codepen](https://codepen.io/susir/pen/vxWypq) _(note: right click both for new tab!)_


### Hello World exercise - You do!
#### Code along: Adding props to our component

Let's use **props** to make our "Hello World" app more flexible.

##### First, a single prop

We want to make a greeting that's reusable for many different users, so we'll have a `name` prop for the name of the user.

In your `src/index.js`, we'll change the line that renders the `Hello` component to include this `name` prop. The new line will be:

`<App name={"Carl Sagan"} />`

> We pass in data wherever we are rendering our component. In rendering the `App` component above, we pass in a prop called "name" with a value of "Carl Sagan".

Your `index.js` should now look like this:

```js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';

ReactDOM.render(<App name={'Carl Sagan'} />, document.getElementById('root'));
```

Now, every time we render our component, we will pass in data.
- When the `App` component renders, we pass the `App` component a prop called `name` with a value of `Carl Sagan`.

If you check your application now, nothing has changed.  We're passing the `name` prop into the component, but the component isn't _using_ it yet.

First, we need to pass in the `props` object to our `App` component like so:

`export default function App(props) {`

In our component definition, we will change the `<h1>Hello World!</h1>` to `<h1>Hello {props.name}!</h1>`. The portion `{props.name}` deserves a closer look:

- `props` will collect all the props for this component instance
- `props.name` pulls out the name property from `props`.

> The `{}` syntax in JSX renders the result of any expression inside it. It works even without props. If you wrote `{2+2}` in your JSX, `4` would be rendered.

In `App.js`, your `Hello` class should now look like this:

```jsx
import React from 'react';
import './style.css';

export default function App(props) {
  return (
    <div>
      <h1>Hello {props.name}</h1>
      <p>Start editing to see some magic happen :)</p>
 		<h3>It's time for tea.</h3>
    </div>
  );
}
```

In the above example, we replaced "world" with `{props.name}`.


![](https://i.imgur.com/kJBLdsb.png)

<br>

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Multiple Props


## What about... multiple props?

Of course, we often want components to display more complex information. To do so, we can pass multiple properties to our component! We'll use the same two steps we took to add the first prop.

First, add another prop to the component call: `<App name={"Carl Sagan"} />,` changes to `<App name={"Carl Sagan"} age={62} />`.

Update your `index.js` file to reflect this:

```js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';

ReactDOM.render(
  <App name={'Carl Sagan'} age={62} />,
  document.getElementById('root')
);
```

Now, in our component definition we have access to both values.  The second step is to change the `App` component class in `App.js` to use the age information!


```js
import React from 'react';
import './style.css';

export default function App(props) {
  return (
    <div>
      <h1>Hello {props.name}</h1>
      <p>You are {props.age} years old.</p>
    </div>
  );
}
```


## What about... multiple props passed from an object?

If we have many props, it might get difficult to keep track when we're passing everything in to render a component. A better practice is to organize values in some kind of object and then pass props to the component from that object. Let's see this strategy.

Currently, in `index.js`, we put Carl Sagan's name and age directly into the `ReactDOM.render` call. Instead, we'll create an object that holds Carl Sagan's name and age, making it clearer for other developers and easier to change in the future. In your `index.js file`, below the `import` statements, add this object definition:

``` js
const person = {
  personName: "Carl Sagan",
  personAge: 62
}
```

Next, we'll update what's passed into the component. Near the bottom of your `index.js`, modify the `ReactDOM.render()` call:

``` js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';

const person = {
  personName: 'Carl Sagan',
  personAge: 62
};

ReactDOM.render(
  <App name={person.personName} age={person.personAge} />,
  document.getElementById('root')
);
```

We don't have to change anything in `App.js`, because it's still receiving exactly the same values for exactly the same two props - `name` and `age`. We're just sending it those values in a slightly different way.

> Try changing the values inside the `person` object without changing the `ReactDOM.render()` call. See how the page updates.


#### Multiple props from a more complex object

Since we're just pulling props out of an object, we can use any object we want. For example, we can nest an array inside it.

Let's say our user has some favorite animals. Update your object to include an array:


``` js
const person = {
  personName: "Carl Sagan",
  personAge: 62,
  favorites: [
    "Birds",
    "Tigers",
    "Dinosaurs count!"
  ]
}
```

Now we can use this new information as a prop, just like normal. You could choose to pass a single element (`favorites[0]`) or the entire array.  We'll use the entire array so that the component can display _all_ a person's favorite animals. First, update your `ReactDOM.render()` call in `index.js`:


``` js
import React from 'react';
import ReactDOM from 'react-dom';

import App from './App';

const person = {
  personName: 'Carl Sagan',
  personAge: 62,
  favorites: ['Birds', 'Tigers', 'Dinosaurs count!']
};

ReactDOM.render(
  <App
    name={person.personName}
    age={person.personAge}
    animals={person.favorites}
  />,
  document.getElementById('root')
);
```

If you check your application now, nothing has changed. Remember, a component class will just ignore any props it receives that it doesn't use. But, we want to use the favorite animals! So, second, update your `App` class `render` method in `App.js`:

```html
import React from 'react';
import './style.css';

export default function App(props) {
  return (
    <div>
      <h1>Hello {props.name}</h1>
      <p>You are {props.age} years old.</p>
      <p>You love: {props.animals}</p>
    </div>
  );
}
```

If you check the page now, you'll see React prints the entire array, as that's what was passed in. If we wanted to include all the animals clearly, we could fix the spacing. Instead, to review some syntax, let's just modify the code to render the first value.

```html
import React from 'react';
import './style.css';

export default function App(props) {
  return (
    <div>
      <h1>Hello {props.name}</h1>
      <p>You are {props.age} years old.</p>
      <p>You love: {props.animals[0]}</p>
    </div>
  );
}
```

Check it out!

*[Read more about using props in JSX, if you'd like!](https://facebook.github.io/react/docs/jsx-in-depth.html) This link is also in the Further Reading page at the end of the React module, under the Facebook documentation.*

<br>

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) You Do: A Blog Post

Let's have some practice creating a React component from scratch. How about a blog post?

1. Create a `src/Post.js` file and add this:

	```js
	import React from 'react';
	import './style.css';
	
	export default function Post(props) {
	  return (
	    <div>
	      <p>Post Component is working</p>
	    </div>
	  );
	}
	```

1. In `src/App.js`, import and render the `Post` component file like so:

	```js
	import React from 'react';
	import './style.css';
	import Post from './Post';
	
	export default function App(props) {
	  return (
	    <div>
	      <h1>Hello {props.name}</h1>
	      <p>You are {props.age} years old.</p>
	      <p>You love: {props.animals[0]}</p>
	      <Post />
	    </div>
	  );
	}
	```


1. Create a `post` object in `src/App.js` that has the following properties:
    - `title`  (example value: `"Dinosaurs are awesome"`)
    - `author` (example value: `"Stealthy Stegosaurus"`)
    - `body` (example value: `"Check out this body property!"`)
    - `comments` (example value: `["First!", "Great post", "Hire this author now!"]`)

	<details>
	<summary>`post` object</summary>
	
	
	```js
	const post = {
	  title: 'Dinosaurs are awesome',
	  author: 'Stealthy Stegosaurus',
	  body: 'Check out this body property!',
	  comments: ['First!', 'Great post', 'Hire this author now!']
	};
	```
	
	</details>

5. Render a `Post` component with the information from your `post` object as its props values. **For now, only include one of the comments**. You decide how you want to display the title, author, body, and comment, or you can use the screenshot in the Solution section below as inspiration.  

6. Optional: adjust the CSS of your index file body to align your text to the center of the document.

<br>

## Loop over `comments`

`App.js`

```js
import React from 'react';
import './style.css';
import Post from './Post';

const post = {
  title: 'Dinosaurs are awesome',
  author: 'Stealthy Stegosaurus',
  body: 'Check out this body property!',
  comments: ['First!', 'Great post', 'Hire this author now!']
};

export default function App(props) {
  return (
    <div>
      <h1>Hello {props.name}</h1>
      <p>You are {props.age} years old.</p>
      <p>You love: {props.animals[0]}</p>
      <Post author={post.author} comments={post.comments} />
    </div>
  );
}
```

`Post.js`

```js
import React from 'react';
import './style.css';

export default function Post(props) {
  return (
    <div>
      <p>Post Component is working</p>
      <p>{props.author}</p>
      <ul>
        {props.comments.map(comment => (
          <li>{comment}</li>
        ))}
      </ul>
    </div>
  );
}
```

<br>

## Add State

[Using the State Hook](https://reactjs.org/docs/hooks-state.html)


`App.js`

```js
import React, { useState } from 'react';
import './style.css';
import Post from './Post';

const post = {
  title: 'Dinosaurs are awesome',
  author: 'Stealthy Stegosaurus',
  body: 'Check out this body property!',
  comments: ['First!', 'Great post', 'Hire this author now!']
};

export default function App(props) {
	// variable, event handler
  const [count, setCount] = useState(0);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
      <h1>Hello {props.name}</h1>
      <p>You are {props.age} years old.</p>
      <p>You love: {props.animals[0]}</p>
      <Post author={post.author} comments={post.comments} />
    </div>
  );
}
```

## Bonus - add `Comment` Component

`Comment.js`

```js
import React from 'react';
import './style.css';

export const Comment = props => (
  <div>
    <li>{props.comment}</li>
  </div>
);
```

`Post.js`

```js
import React from 'react';
import './style.css';
import { Comment } from './Comment';

export default function Post(props) {
  return (
    <div>
      <p>Post Component is working</p>
      <p>{props.author}</p>
      <ul>
        {props.comments.map(comment => (
          <Comment comment={comment} />
        ))}
      </ul>
    </div>
  );
}
```

<br>

## Additional Resources

- [React Docs](https://reactjs.org/docs/getting-started.html)
- [React Tutorial](https://reactjs.org/tutorial/tutorial.html)

