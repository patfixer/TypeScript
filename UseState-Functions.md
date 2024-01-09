### with JSX
# Updater function:
A function passed as an argument to set an object to setState() sometimes it think
that the state is not updated immediately, so we use this updater function. Asynchronous
functions are a good practice to use.


`import { useState } from "react"` This is a hook why not useHook really but not it a useState hook 

Safer to use arrow function that assigned c 
`setCount(c => c +1 )` Updates

```js
import { useState } from "react"


function App() {
  const [count, setCount] = useState(10)

  
  function increment(){
    setCount(c => c +1 )
    setCount(c => c +1 )
     
  }

  function decrement(){
    setCount(c => c -1 )
  }

  function reset(){
    setCount(c => c = 0)
  }

   return (
    <>
    <div>
      <p>Count: {count}</p> 
      <button onClick={increment}>Increment</button>
      <button onClick={reset}>Reset</button>
      <button onClick={decrement}>Decrement</button>
    </div>
    </>
   ) 
}

export default App
```


# onChange={} Method
```js
import { useState } from "react"


function App() {
  const [key, terms] = useState({
    FSB: "Font side bus",
    HDD: "Hard disk drive",
    MHz:300
  }) 
   
  // Im creating a call back to change number in input
  function mhzChange(event){
    // You need braces () To create an object to modify 
    // the pervious state of MHz we use the updater function => 
        terms(t => ({...t, MHz: event.target.value}))
  }

  function fsbChange(event){
    terms(t => ({...t, FSB: event.target.value}))
  }

  function hddChange(event){
    terms(t => ({...t, HDD: event.target.value}))
  }
   // This is the onChange={} method used inside the input element
   return (
    <>
    <div>
      <p> Mhz {key.MHz} </p> 
      <input type="number" value={key.MHz} onChange={mhzChange}/> 
      <input type="text" value={key.FSB} onChange={fsbChange}/>
      <input type="text" value={key.HDD} onChange={hddChange}/>
      
    </div>
    </>
   ) 
}




export default App
```

### The useCallback Hook used to update text
# onChange events:
Using a event handler in forms elements `<input>, <textarea>, <radio> <select>`
This will trigger a function when the value in the input changes
```js
import { useState } from "react"

function App() {
  
  const [name, setName] = useState("")

  function change(event){
    setName(event.target.value)
  }
  
   return (<div>
    <input type="text" value={name} onChange={change} />
    <p>Change Here: {name}</p>
   </div>) 
}

export default App
```

# Added const [quantity, setQuantity] = useState()
```js
import { useState } from "react"

function App() {
  
  const [name, setName] = useState("User")
  const [quantity, setQuantity] = useState()

  function change(event){
    setName(event.target.value)
  }
 
  function quantityChange(event){
    setQuantity(event.target.value)
  }
  
   return (<div>
    <input type="text" value={name} onChange={change} />
    <p>Change Here: {name}</p><br />
    <input type="number" value={quantity} onChange={quantityChange}/>
    <p>Numbers: {quantity}</p>
   </div>) 
}

export default App
```
