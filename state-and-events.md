[Home](https://github.com/wgoode3/react-notes/blob/master/README.md)
[Prev](https://github.com/wgoode3/react-notes/blob/master/create-react-app.md)

## State

In react, ```state``` is where we store key information about our app so that we can display it to our users in the ```render()``` method and make appropriate changes to it as the user interacts with our app.

We can create a state attribute inside of the [contructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes) of our class. If we have a message to display to our users, we could put something like this into our ```App.js```.

```javascript
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            message: "Welcome to the site!"
        };
    }

    render() {
        return (
            <div>
                <h1>{this.state.message}</h1>
            </div>
        );
    }
}
```

When this app component is rendered, it will display our message ```"Welcome to the site!"``` to the user inside of the ```<h1>{this.state.message}</h1>```. If we change ```this.state.message``` to instead say ```"Goodbye friend!"``` it will show that message instead inside the ```<h1>``` tag.

This will prove useful for us, as we may in the future have more complicated things stored inside of ```state``` like a list of products a user could buy or messages a user has received from their friends.

## Events

State on it's own isn't too impressive to us, we could just have easily added the message directly into the ```<h1>``` tag to display it to our users. Where state shines is allowing us to change it based on a user interacting with our site. For our user to interact with our site, we will need to introduce events. The simplest event we can choose is the user clicking on something in our app.

For this example, we are going to have a button that let's a user "leave" our app. We haven't implemented any sort of user authentication, this is just a simple example to show how we can change state.

We will start with the above example and add in a new method called ```logout()```, and also add a corresponding button into our ```render()``` method.

```javascript
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            message: "Welcome to the site!"
        };
    }

    logout = (e) => {
        this.setState({message: "Goodbye friend!"});
    }

    render() {
        return (
            <div>
                <h1>{this.state.message}</h1>
                <button>Leave</button>
            </div>
        );
    }
}
```

In order to change what we have stored in ```state```, React will make us use the method ```this.setState()```. We could mutate the values stored in ```state``` directly (ie ```this.state.message = "something else";```), however this is bad practice and could get us in trouble later.

In the above example, we also need to add in one more thing. Currently the ```leave``` button isn't associated with the ```logout``` method at all. We need to use the "click" event to associate them. This can be added directly in the ```render()``` method...

```javascript
<button onClick={this.logout}>Leave</button>
```

Now when a user clicks on the ```leave``` button it will run the ```logout``` method and change the text that is displayed.

[Next](https://github.com/wgoode3/react-notes/blob/master/child-components-and-props.md)
