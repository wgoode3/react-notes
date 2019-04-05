# React Notes

#### Contents
link to various lessons here

## Create Element

Assuming we have the following in our ```index.html```.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <script src="node_modules/react/umd/react.development.js"></script>
    <script src="node_modules/react-dom/umd/react-dom.development.js"></script>
    <title>React Demo</title>
</head>
<body>
    <div id="root"></div>
    <script type="text/babel" src="app.js"></script>
</body>
</html>
```

And the following in our ```app.js```.

One way to create react elements is to use ```React.createElement()```. Using this we can identify:
1. what type of html element we want (in the below case an ```h1``` tag)
2. the ```props``` to pass to the element (we'll discuss this more later)
3. the children of the element (in this case just text) 

Next we'll use ReactDOM to place this component into the page, whererever the element with ```id="root"``` is located.

```javascript
const greeting = React.createElement(
    "h1",
    null,
    "Hello World!"
);
ReactDOM.render(greeting, document.getElementById("root"));
```

If for instance we wanted to make a list, we could do something similar...

```javascript
const myList = React.createElement(
    "ul",
    null,
    [
        React.createElement("li", null, "Learn React"),
        React.createElement("li", null, "Learn MongoDB"),
        React.createElement("li", null, "????"),
        React.createElement("li", null, "Profit!!!")
    ]
)
ReactDOM.render(myList, document.getElementById("root"));
```

This process works, but is rather tedious. If instead we have added the following script to our ```index.html``` we can use the JSX instead of createElement.

```html
<script crossorigin src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

This script will add ```babel``` which can **transpile** (convert one type of code into another) our JSX code into vanilla JS.

## JSX

JSX (JavaScript XML) is an extension to JavaScript that allows us to write code that closely resembles HTML without having to make it a string. This is the preferred way to use React. Using JSX we can rewrite the above examples like so...

```javascript
const text = "Hello World"
const greeting = <h1>{text}</h1>
ReactDOM.render(greeting, document.getElementById("root"));
```

and 

```javascript
const todos = ["Learn React", "Learn MongoDB", "????", "Profit!!!"];
const myList = <ul>
    {
        todos.map( (item, index) => 
            <li key={index}>{item}</li>
        )
    }
<ul>;
ReactDOM.render(myList, document.getElementById("root"));
```

This allows us to more easily write the code that will be displayed to users, and affords us an easy way to work in view logic that we are familiar with from other templating languages (Jinja2 in Python, JSP in Java, or Razor in C#).

### Overcoming CORS 

We may run into CORS (Cross-Origin Resource Sharing) errors when we try the examples above using the link to ```babel.min.js```. The best way to deal with this issue, is to not open the ```index.html``` file directly in our browser, but to instead serve it using a webserver. In the not-so-distant future this may be the Node.js/Express/Mongo server that will make up the back-end of our ```MERN``` stack, but for now the simplest http server we can use is python's ```http.server```.

```shell
cd ~/directory/to/your/project
python3 -m http.server 8000
```

Simply change directory into the folder that contains your project, and ```http.server``` will serve the ```index.html``` file at localhost:8000.

## create-react-app

Now that we have gotten our feet wet using React and using JSX, we could really use a nice tool to set up our projects for us. We've also probably seen a warning in our console when we use the ```babel``` script link letting us know this will not be a suitable solution in a production environment. 

Enter [create-react-app](https://github.com/facebook/create-react-app). This tool does exactly what it sounds like it does, it creates react apps. 

We can install ```create-react-app``` using the following command (assuming npm is installed)...

```shell
npm i -g create-react-app
```

You will need to use ```sudo``` if you get errors relating to permissions on MacOS or GNU/Linux.

When we go to run this, we can invoke ```create-react-app``` directly in the command line to make our app, however this has been a very slow process (sometimes longer than 3 minutes) each time we make an app in react.

```shell
create-react-app my-app
```

 To speed this up we can use [Yarn](https://yarnpkg.com/en/docs/install). Follow the instructions to install it, then we can use it to make ```create-react-app``` run a lot faster.

```shell
yarn create react-app my-app
```

However we choose to run ```create-react-app```, it will create a folder structure that looks like the following.

```
├─ my-app
┊ ├─ node_modules
┊ ├─ public
┊ ┊ ├─ favicon.ico
┊ ┊ ├─ index.html
┊ ┊ ├─ manifest.json
┊ ├─ src
┊ ┊ ├─ App.css
┊ ┊ ├─ App.js
┊ ┊ ├─ index.css
┊ ┊ ├─ index.js
┊ ┊ ├─ serviceWorker.js
├─ package.json

# some files and folders removed for brevity
```

We can run the newly created ```my-app``` by changing directory into it, and telling npm to start the project.

```shell
cd my-app
npm start
```

This will run ```my-app``` in a test server on port 3000. We can view the react app by navigating our browser to localhost:3000.