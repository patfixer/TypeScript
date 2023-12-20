# Keep In Mind You Using JSX Typescript 
JSX uses mapping like a for each loop  

`{}` The curly braces render context dynamic

`terms.map(term => <li>{term}</li>)` Converting elements

`<Fragment>` -More than one html tag <h1> <label> 
# ListGroup Function
```js
import { Fragment } from "react"

function ListGroup() {
    return( 
    <Fragment>
        <h2>Terms</h2>
        <ul className="list-group">
        <li className="list-group-item">PC</li>
        <li className="list-group-item">Hardware</li>
        <li className="list-group-item">ATX</li>
        <li className="list-group-item">SDRAM</li>
        <li className="list-group-item">CLUSTER</li>
          </ul>
    </Fragment>)
}
 
export default ListGroup
```

# App.tsx
### imported in main.tsx 
Returns <ListGroup /> 
```js
// import './App.css'
import ListGroup from "./components/ListGroup"

function App() {
  

  return (
    <>
      <div>
        <ListGroup />
      </div>
    </>
  )
}

export default App
```

`{terms.map(term => <li>{term}</li>)}` Mapping array term dynamically using `{}` braces
```js
import { Fragment } from "react"

function ListGroup() {
 const terms = [
    'PC',
    'Hardware',
    'ATX',
    'SDRAM',
    'CLUSTER'
 ]


    return( 
    <Fragment>
        <h2>Terms</h2>
        <ul className="list-group">
          {terms.map(term => <li>{term}</li>)}
          </ul>
    </Fragment>)
}

export default ListGroup
```

`let list = terms.map(term => <li>{term}</li>)` list is your assigned to terms map or mapping which iterate over the array of list and creates an 
element <li> For each term, which uses `key={term}` this `{terms.map(term => <li key={term}>{term}</li>)}` identifier that help update 
the rending process for each individual term in the array. 

# JSX:
```js
import { Fragment } from "react"
const fantasy = {ghost:"Not Here"}


function ListGroup() {
 let terms = [
    'PC',
    'Hardware',
    'ATX',
    'SDRAM',
    'CLUSTER'
 ]
 terms = []

 if (terms.length === 0){
    return <p>{fantasy.ghost}</p>
 }
 
    return( 
    <Fragment>
        <h2>Terms</h2>
        <ul className="list-group">
          {terms.map(term => <li key={term}>{term}</li>)}
          </ul>
    </Fragment>)
}

export default ListGroup
```

# OnClick{() => arrow function}
A trigger `onClick={() => console.log("Clicked")` an event handler in React will log to console Clicked. 

`<li className="list-group-item" key={term} onClick={() => console.log("Clicked")}>{term}</li>` 

### Key={<li>new element</li>}
The `key={term}` attribute is set to value=term helps in rendering process
`terms.map(term => <li key={term}>{term}</li>)`  Key `{term}` a identifier iterates creating elements to be rendered

`let list = terms.map(term => <li>{term}</li>)` Mapping list with arrow function `=>` 

```js
{terms.map(term => <li className="list-group-item" key={term} onClick={() => console.log("Clicked")}>{term}</li>)}
```

```js
import { Fragment } from "react"


function ListGroup() {
 let terms = [
    'PC',
    'Hardware',
    'ATX',
    'SDRAM',
    'CLUSTER'
 ]

    return( 
    <Fragment>
        <h2>Terms</h2>
        {terms.length === 0 && <h1>&#9731;</h1>}
        <ul className="list-group">
          {terms.map(term => <li className="list-group-item" key={term} onClick={() => console.log("Clicked")}>{term}</li>)}
          </ul>
    </Fragment>)
}

export default ListGroup
```

# Outside The Function
### Mapping can used outside of the function if needed 
```js
const list = terms.map(term => <li className="list-group-item" key={term} onClick={() => console.log("Clicked")}>{term}</li>)

function ListGroup() {
    return( 
    <Fragment>
        <h2>Terms</h2>
        {terms.length === 0 && <h1>&#9731;</h1>}
        <ul className="list-group">
          {list}
          </ul>
    </Fragment>)
}

export default ListGroup
```

# Arrow function 
```js
const inside = () =>{
   return terms.map(term => <li className="list-group-item" key={term} onClick={() => console.log("Clicked")}>{term}</li>)
}

const basic = () => {
   return terms.length === 0 && <h1>&#9731;</h1>
}
```

# Change on console.log("Clicked") to console.log(term)
`terms.map(term => <li className="list-group-item" key={term} onClick={() => console.log("Clicked")}>{term}</li>)`  This is where the `key={term}` come in this identifies the elements in the array: `onClick={()}`
```js
 let terms = [
    'PC',
    'Hardware',
    'ATX',
    'SDRAM',
    'CLUSTER'
 ]
```
