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
        let p = {...this.state.prduct};
        p.name = e.target.value;
        this.setState({product: p});
    }

    changePrice = (e) => {
        let p = {...this.state.prduct};
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

We make use of the JavaScript [spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax) operator to clone the information strored in state, rather than make a new pointer to the location of the information in state. 



\[Next\]