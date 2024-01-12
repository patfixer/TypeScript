
# This is a more final version 

This use state method to create a list of 3 items
```js 
const [addTo, setToList] = useState(["lamp", "watch", "phone"]);
```

`useState("")` A method to create an empty input box.

```js
function List() {
    const [addTo, setToList] = useState(["lamp", "watch", "phone"]);
    const [newList, setNewList] = useState("")
```

`const [addTo, setToList]` addTo the array and setToList to update the array

`const [newList, setNewList]` newList is the input box and setNewList is to update the input box


 This is needed the event inside the parameters 
```js
function inputChange(event) {
        setNewList(event.target.value)
    }
```

`setNewList(event.target.value)` this target the value of the input box


 A function called addToList. 

```js
function addToList() {
        setToList([...addTo, newList]);
        setNewList("");
    }
```
 
`setToList([...addTo, newList]);` Inside the function we are updating the addTo array with the newList and then we are updating the newList to an empty string, which is `setNewList("");`.

`function deleteFromList(index){}` A function called deleteFromList.

`const updateList = addTo.filter((item, i) => i !== index);` We are filtering the addTo array by the index and then we, update the addTo array with the updateList.

 
`function moveUp(index){}` A function called moveUp.    


```js
function deleteFromList(index) {
        const updateList = addTo.filter((item, i) => i !== index);
        setToList(updateList);
    }
```


`if (index > 0) {}` If the index is greater than 0, we are doing the following:

```js
function moveUp(index) {
        if (index > 0) {
            const updateUp = [...addTo];
            [updateUp[index], updateUp[index - 1]] = [updateUp[index - 1], updateUp[index],];
            setToList(updateUp);
        }
    }
```

`const updateUp = [...addTo];` We are creating a new array called updateUp and we are assigning the addTo array to it.

`[updateUp[index], updateUp[index - 1]] = [updateUp[index - 1], updateUp[index]` We are swapping the values of the index and the index - 1.

`setToList(updateUp);` We are updating the addTo array with the updateUp array.

`function moveDown(index){}` A function called moveDown.

`if (index < addTo.length - 1) {}` If the index is less than the length of the addTo array minus 1,

`const updateDown = [...addTo];` We are creating a new array called updateDown and we are assigning the addTo array to it.

`[updateDown[index], updateDown[index + 1]] = [updateDown[index + 1], updateDown[index]` We are swapping the values of the index and the index + 1.

`setToList(updateDown);` We are updating the addTo array with the updateDown array.

```js
import React, { useState } from "react";


function List() {
    const [addTo, setToList] = useState(["lamp", "watch", "phone"]);
    const [newList, setNewList] = useState("")

    function inputChange(event) {
        setNewList(event.target.value)
    }

    function addToList() {
        setToList([...addTo, newList]);
        setNewList("");
    }

    function deleteFromList(index) {
        // item something to be ignored like an underscore
        const updateList = addTo.filter((item, i) => i !== index);
        setToList(updateList);
    }

    function moveUp(index) {
        if (index > 0) {
            const updateUp = [...addTo];
            [updateUp[index], updateUp[index - 1]] = [updateUp[index - 1], updateUp[index],];
            setToList(updateUp);
        }
    }

    function moveDown(index) {
        if (index < addTo.length - 1) {
            const updateUp = [...addTo];
            [updateUp[index], updateUp[index + 1]] = [updateUp[index + 1], updateUp[index],];
            setToList(updateUp);
        }
    }

    return (<>
        <div className="todo-list">
            <h1>Remember what to do</h1>
            <input
                type="text"
                placeholder="Add to list"
                onChange={inputChange}
                value={newList}
            />
            <button className="add-button" onClick={addToList}>Add</button>
        </div>
        <ol>
            {addTo.map((item, index) => <li key={index}>
                <span className="text">{item}</span>
                <button className="delete-button" onClick={() => deleteFromList(index)}>Remove &#129356;</button>
                <button className="move-button" onClick={() => moveUp(index)}>Up &#129351;</button>
                <button className="move-button" onClick={() => moveDown(index)}>Down &#129352; </button>
            </li>)}
        </ol>
    </>)
}

export default List;
```
