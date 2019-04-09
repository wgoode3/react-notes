[Home](https://github.com/wgoode3/react-notes/blob/master/README.md)
[Prev](https://github.com/wgoode3/react-notes/blob/master/child-components-and-props.md)

## Forms

As we start working on more full-featured apps, one common element that we'll frequently need to deal with are forms. There are more than a few ways to handle forms in React, but generally we will want to use the ```onChange``` event to update information in ```state``` when the user makes changes to the inputs. We'll also use the ```onSubmit``` event on the ```<form>``` to handle what to do with the data in state when the user clicks the button to submit the form.

```javascript
class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            product: {
                "name": "",
                "price": 0
            }
        };
    }

    newProduct = (e) => {
        e.preventDefault();
        alert(`{name: ${this.state.name}, price: ${this.state.price}}`);
    }

    changeName = (e) => {
        let p = {...this.state.product};
        p.name = e.target.value;
        this.setState({product: p});
    }

    changePrice = (e) => {
        let p = {...this.state.product};
        p.price = e.target.value;
        this.setState({product: p});
    }

    render() {
        return (
            <form onSubmit={this.newProduct}>
                <p>
                    Name:
                    <input 
                        type="text" 
                        name="name" 
                        onChange={this.changeName} 
                    />
                </p>
                <p>
                    Price:
                    <input
                        type="number"
                        name="price"
                        step="0.01"
                        min="1"
                        onChange={this.changePrice}
                    />
                </p>
                <input type="submit" />
            </form>
        );
    }
}
```

When the user types the name of a product into the "Name" input, whenever that input changes it will call the ```this.changeName``` method in the App class. That class will then make a variable ```p``` and set it equal to a copy of the information stored in ```this.state.product```. 

```javascript
let p = {...this.state.product};
```

We make use of the JavaScript [spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) operator to clone the information strored in state, rather than make a new pointer to the location of the information in state. Next we change the name attribute in the ```p``` variable to set it equal to the data from our form.

```javascript
p.name = e.target.value;
```

The variable ```e``` is a synthetic event variable, the ```.target``` attribute is the ```<input />``` element itself and the ```.value``` is the value currently entered into the input. Lastly we run ```setState()``` to alter the ```product``` we're keeping track of in ```this.state``` to reflect what we changed on our variable ```p```.

```javascript
this.setState({product: p});
```

We do essentially the same process for ```price``` and any other inputs that we would have. When the user goes to submit the form, the ```newProduct``` method is called. The first thing we need to do is prevent the form from actually submitting anywhere (we want to handle this ourselves), so we call ```.preventDefault()``` on the synthetic event ```e```. After this we could do whatever we want to with our form date; to visualize this easily, let's use ```alert()``` to pop up the information in a prompt. Later we may want to pass this information into an array of products instead or even save it to a database with our REST server.

[Next](https://github.com/wgoode3/react-notes/blob/master/lifting-state.md)