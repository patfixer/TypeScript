# Keep In Mind You Using JSX Typescript 
JSX uses for loops with other method which makes scene is why I find 
the syntax different 

`{}` The curly braces renders dynamic context

`terms.map(term => <li>{term}</li>)` Converting list is looping throught the array of elements  

`<Fragment>` With this Fragment you can have more than one HTML tag <h1> <label> 
# ListGroup
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

# Mapping like for each loop 
`{terms.map(term => <li>{term}</li>)}`  
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
        <label>Not Sure</label>
        <h2>Terms</h2>
        <ul className="list-group">
          {terms.map(term => <li>{term}</li>)}
          </ul>
          <br />
          <input type="text" id="check" />
    </Fragment>)
}

export default ListGroup
```
