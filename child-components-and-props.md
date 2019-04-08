[Home](https://github.com/wgoode3/react-notes/blob/master/README.md)
[Prev](https://github.com/wgoode3/react-notes/blob/master/state-and-events.md)

## Child Components and Props

When we're working with our ```app.js``` we may find ourselves at times writing repetative code. For instance imagine we have a list of products we want to show to our users.

```javascript
class App extends Component {
    render() {
        return (
            <div className="container">
                <h1 className="jumbo">React Store!</h1>
                <div className="product">
                    <h3>Name: Coffee Mug</h3>
                    <p>Price: $8.99</p>
                    <input type="number" name="quantity0" min="0" max="10" />
                    <button>Add to Cart</button>
                </div>
                <div className="product">
                    <h3>Name: Mouse Pad</h3>
                    <p>Price: $15.49</p>
                    <input type="number" name="quantity1" min="0" max="10" />
                    <button>Add to Cart</button>
                </div>
                <div className="product">
                    <h3>Name: Monitor Stand</h3>
                    <p>Price: $24.99</p>
                    <input type="number" name="quantity2" min="0" max="10" />
                    <button>Add to Cart</button>
                </div>
            </div>
        );
    }
}
```

This involves writing a lot of the same code over and over again. If we want to add in another product to our store, we'd have to make yet another div and put all of the information in again. One of the most powerful advantages that React and other component based architecture frameworks give us, is that we can essentially make our own html elements (Web Components) to do this for us. We can make them take in the right information and display it in the right places.

Using child components, we can rewrite the above example like so...

```javascript
class Product extends Component {
    render() {
        return (
            <div className="product">
                <h3>{this.props.product.name}</h3>
                <p>{this.props.product.price}</p>
                <input type="number" name="quantity" min="0" max="10" />
                <button>Add to Cart</button>
            </div>
        );
    }
}

class App extends Component {
    render() {
        return (
            <div className="container">
                <h1 className="jumbo">React Store!</h1>
                <Product product={{name: "Coffee Mug", price: "$8.99"}} />
                <Product product={{name: "Mouse Pad", price: "$15.49"}} />
                <Product product={{name: "Monitor Stand", price: "$24.99"}} />
            </div>
        );
    }
}
```

Notice how much shorter this is to write. We can add a child component in as if it is it's own html element ```<Product />```, pretty cool huh? Also notice how we've had to add in a new attribute (think like adding an src and alt tag to an image ```<img src="myimg.jpg" alt="my image" />```) and we have called it "product" and set it equal to a javascript object containing name and price information. This is how we get name and price into each ```<Product />``` child component. These are called ```props```, information that we pass down from the parent into child components. We access them inside the child component by going through ```this.props```.

If we're feeling adventurous, we can consider storing all of the product information inside of the ```state``` of our App component. We can then use ```.map()``` to loop through the array of product information and return a new array of ```<Product />``` child components. We can pass the product ```prop``` and the index as ```key``` (React uses key internally) to each child component.

```javascript
// the Product class is unchanged from the previous example

class App extends Component {
    constructor(props){
        super(props);
        this.state = {
            products: [
                {name: "Coffee Mug", price: "$8.99"},
                {name: "Mouse Pad", price: "$15.49"},
                {name: "Monitor Stand", price: "$24.99"}
            ]
        };
    }

    render() {
        return (
            <div className="container">
                <h1 className="jumbo">React Store!</h1>
                {
                    this.state.products.map( (aProduct, index) =>
                        <Product key={index} product={aProduct} />
                    );
                }
            </div>
        );
    }
}
```

[Next](https://github.com/wgoode3/react-notes/blob/master/forms.md)