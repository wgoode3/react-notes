[Home](https://github.com/wgoode3/react-notes/blob/master/README.md)
[Prev](https://github.com/wgoode3/react-notes/blob/master/forms.md)

## Lifting up State

Consider what would happen if we have the following app...

```javascript
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            groceries: [
                "Carrots",
                "Cremini Mushrooms",
                "Beef Stock",
                "Pearl Onions"
            ],
            item: ""
        }
    }

    onChange = (e) => {
        this.setState({item: e.target.value});
    }

    onSubmit = (e) => {
        e.preventDefault();
        let items = [...this.state.groceries];
        items.push(this.state.item);
        this.setState({groceries: items});
    }

    render() {
        return (
            <div className="container">
                <ul>
                    {
                        this.state.groceries.map( (item, index) => 
                            <li key={index}>{item}</li>
                        )
                    }
                </ul>
                <form onSubmit={this.addItem}>
                    <input 
                        type="text" 
                        name="item" 
                        onChange={changeItem} 
                    />
                    <input type="submit" />
                </form>
            </div>
        );
    }
}
```

This app allows us to add items to a groceries list. If we decide that we want to modularize this, we can take the ```<ul>``` and make it it's own component.

```javascript

class GroceryList extends Component {
    render(){
        return (
            <ul>
                {
                    this.props.arr.map( (item, index) => 
                        <li key={index}>{item}</li>
                    )
                }
            </ul>
        );
    }
}
```

We could also take out the form an make it it's own component as well.

```javascript
class GroceryForm extends Component {
    constructor(props){
        super(props);
        this.state = {
            item: ""
        }
    }

    changeItem = (e) => {
        this.setState({item: e.target.value});
    }

    addItem = (e) => {
        e.preventDefault();
        // what do we do with the item now?
    }

    render() {
        return (
            <form onSubmit={this.addItem}>
                <input 
                    type="text" 
                    name="item" 
                    onChange={changeItem} 
                />
                <input type="submit" />
            </form>
        );
    }
}
```

Which will allow us to rewrite our ```App``` component like so...

```javascript
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            groceries: [
                "Carrots",
                "Cremini Mushrooms",
                "Beef Stock",
                "Pearl Onions"
            ]
        };
    }

    addItemToList = (item) => {
        // when does this get run? where does item come from
        let items = [...this.state.groceries];
        items.push(item);
        this.setState({groceries: items});
    }

    render() {
        return (
            <div class="container">
                <GroceryList arr={this.state.groceries} />
                <GroceryForm />
            </div>
        );
    }
}
```

For the list, we can pass the array of groceries to the ```GroceryList``` component as a ```prop```, one we have decided to call ```arr```. However, when someone fills out the form in ```GroceryForm``` it isn't clear how to pass that item back to the parent ```App``` component.

The solution is that we can use props to pass this information back up.
We can rewrite the ```render()``` in our ```App``` to add a new ```prop```.

```javascript
render() {
    return (
        <div class="container">
            <GroceryList arr={this.state.groceries} />
            <GroceryForm onAddItem={this.addItemToList} />
        </div>
    );
}
```

This time the ```prop``` isn't data like an array or an object or a string, but a function ```this.addItemToList()```. This will act as a callback function, one that we can pass a variable into (the item the user is adding). Now we just need to rewrite our ```addItem()``` method in our ```GroceryForm``` component to have it call this callback function and pass our item into it.

```javascript
addItem = (e) => {
    e.preventDefault();
    this.props.onAddItem(this.state.item);
}
```

\[Next\]