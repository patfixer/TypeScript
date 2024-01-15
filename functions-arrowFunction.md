# Functions And Arrow Function 
Arrow function `const nameChange = (event) => {}` seem be Similar to regular functions  `function change(event){}`
```js
import { useState } from "react"

function Summary() {
    const [name, setName] = useState("")

    const nameChange = (event) => {
        setName(event.target.value)
    }

    const [fav, setFav] = useState("")
    
    function change(event) {
        setFav(event.target.value)
    }

    return (<>
        <br /><br />
        <button onClick={() => handle()}>Add</button>
        <br /><br />
        <input type="text" value={name} onChange={nameChange} />
        <h3>{name}</h3>
        <br /><br />
        <input type="text" value={fav} onChange={change} />
        <h3>{fav}</h3>
    </>)
}

export default Summary
