# Array and UseStates 
Resetting the input textbox after clicking the add button.
The first method `setName([getName])` will replace the existing arrays of emojis.
Spreaders `[...name, getName]` this will spread the original array, while adding new 
values to the array.
```js
import { useState } from "react";

const okay = {
    right: <h1>&#128077;</h1>, wrong: <h1>&#128078;</h1>,
    fire: <h1>&#128293;</h1>, dash: <h1>&#128168;</h1>
}

function Text() {
    const [name, setName] = useState([okay.right, okay.dash, okay.fire])

    function addName() {
        const getName = document.getElementById('name').value
        // Reset input after clicking on the add button
        document.getElementById('name').value = ""

        /* setName([getName]) will add to the array but remove old array 
        and replace this with a new array */

        /*The Spread Operators setName([...name, getName]) 
        Will spread all the useState([okay.right, okay.dash, okay.fire]) values */
        setName([...name, getName])
    }
}
```
But is better to use `setName(n => [...n, getName])` as a parameter don't want `...name` to be;

the same name as `[name, setName]` -Declared useState `const [name, setName] = useState([okay.right, okay.dash, okay.fire])`


```js
import { useState } from "react";

const okay = {
    right: <h1>&#128077;</h1>, wrong: <h1>&#128078;</h1>,
    fire: <h1>&#128293;</h1>, dash: <h1>&#128168;</h1>
}

function Text() {
  /* So im passing the  onClick={() => removeName(index)} to this 
     function removeName(index){}  function.  */
    function removeName(index) {
        /*Here I use the setName and filters the array with an
        underscore filter((_, i) this means to ignore. 
        So when you click on the list will remove from the array */
        setName(name.filter((_, i) => i !== index))
    }
    // 
    return (<>
        <div>
            <input type="text" id="name" placeholder="Maybe Text" /><br />
            <button onClick={addName}>Add</button>
            <br />
            <ul>
                {name.map((nam, index) => <li key={index}
                    onClick={() => removeName(index)}>{nam}</li>)}
            </ul>
        </div>
    </>)
}

export default Text
```

