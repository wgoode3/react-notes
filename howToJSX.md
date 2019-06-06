[Home](https://github.com/wgoode3/react-notes/blob/master/README.md)
[Prev](https://github.com/wgoode3/react-notes/blob/master/create-react-app.md)

## Composing Pages Using JSX

JSX (JavaScript XML) is an extension to JavaScript that allows us to write code that closely resembles HTML without having to make it a string. This is the preferred way to use React.

```javascript
class App extends Component {
    render(){
        return (
            <h1>Hello World</h1>
        )
    }
}
```

Notice how above we make a react component called ```App``` and give it a method called ```render(){ ... }```. This method returns what appears to be an HTML ```<h1>``` tag. Whatever content we wish to make visible on the page, we can write it using a syntax we are already familiar with. 

We are able to use any HTML tags that we are already familiar with, try out some like:

* table
* ul 
* form
* input
* img

### Loops

Consider an example where we have a list of large mammals...

```javascript
class App extends Component {
    render(){
        return (
            <ul>
                <li>Lions</li>
                <li>Whales</li>
                 {/* Many mammals later */}
                <li>Sloths</li>
            </ul>
        )
    }
}
```

This can be cumbersome to write and in many cases we might want to be able to add to or remove from the list easily. Unlike previous frameworks we may be used to, we shouldn't write a ```for``` loop directly, it is preferred to use [.map()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).


```javascript
class App extends Component {
    const mammals = ["Lions", "Whales", "Manatees", "Bears", "Badgers", "Sloths", "Pandas"];
    render(){
        return (
            <ul>
                {
                    mammals.map( (m,i) =>
                        <li key={i}>{m}</li>
                    )
                }
            </ul>
        )
    }
}
```

**Note** React wants us to provide a ```key``` to each child JSX element we create using ```.map()``` and for now the loop index ```i``` will be an appropriate value to give it.

### Conditionals

The easiest way to use conditionals is to use a [ternary operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator). 

```javascript
class App extends Component {
    let myBoolean = true;
    render(){
        return (
            <>
                {
                    myBoolean ? <button>Yes</button> : <button>No</button>
                }
                {
                    myBoolean === false ? <button>Yes</button> : <button>No</button>
                }
            </>
        )
    }
}
```

The above buttons should display...

```
<button>Yes</button>
<button>No</button>
```

### Rules to keep in mind

We aren't free to put in just anything we want to however.

#### JSX Expressions must have one Parent Element

Consider the example code...

```javascript
class App extends Component {
    render(){
        return (
            <h1>Hello World</h1>
            <p>This is a paragraph</p>
        )
    }
}
```

When we are working with JSX, we need to ensure that our code being returned exists inside of one JSX element. The above example will fail to compile with the error message...

```
./src/App.js
  Line 6:  Parsing error: Adjacent JSX elements must be wrapped in an enclosing tag. Did you want a JSX fragment <>...</>?
```

We can either place the above elements inside of a single tag like ```<div>``` or if we don't want to introduce additional elements into the DOM, we are able to make use of a JSX fragment as the error message above alludes to.

```javascript
class App extends Component {
    render(){
        return (
            <>
                <h1>Hello World</h1>
                <p>This is a paragraph</p>
            </>
        )
    }
}
```

#### JSX versions of certain HTML attributes

Consider the following snippet.

```HTML
<h1 class="my-class">This is HTML</h1>
```

If we were to try to use this in JSX, we might come up with something like...

```Javascript
class App extends Component {
    render() {
        return (
            <h1 class="my-class">This is JSX</h1>
        )
    }
}
// wrong
```

But notice how we have class on ```line 1``` and on ```line 4```. This is more than a little ambiguous, and when we're working with JSX, we will get an error in our console telling us...

```
Warning: Invalid DOM property `class`. Did you mean `className`?
    in h1 (at App.js:5)
    in App (at src/index.js:6)
```

When using the HTML class, we will need to instead use the ```className``` attribute in JSX.

```Javascript
class App extends Component {
    render() {
        return (
            <h1 className="my-class">This is JSX</h1>
        )
    }
}
// right
```

Consider the example where we might have a form in HTML.

```HTML
<form action="/process" method="post">
    <div class="form-group">
        <label for="email">Email: </label>
        <input type="text" id="email" name="username" class="form-control" />
    <div>
</form>
```

If we were to rewrite this into JSX, how should it know to handle the ```for``` on ```line 3``` as the HTML version of ```for``` and not as a JavaScript ```for```?

```Javascript
class App extends Component {
    render() {
        return (
            <form action="/process" method="post">
                <div class="form-group">
                    <label htmlFor="email">Email: </label>
                    <input type="text" id="email" name="username" class="form-control" />
                <div>
            </form>
        )
    }
}
```

For more on these differences, please read the excellent [official documentation](https://reactjs.org/docs/dom-elements.html).

[Next](https://github.com/wgoode3/react-notes/blob/master/state-and-events.md)
