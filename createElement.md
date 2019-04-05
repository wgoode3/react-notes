[Home](https://github.com/wgoode3/react-notes/blob/master/README.md)
\[Prev\]

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

[Next](https://github.com/wgoode3/react-notes/blob/master/babel&jsx.md)
