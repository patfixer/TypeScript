
# List This is the start 
This is a basic mapping a list to render `const questionTwo[]` list in Vite using React typescript.
`const` To me this const is like an access modifier when assigned to any variable which can not be changed.
Only with `let` modifier you can change any variable you assign to it. 
```js
function Event(){
   const questionTwo = [
    "Communication between hardware and software.",
    "Video editing and movies.",
    "Input, processing, storage, and output.",
  ];

  
   return(<>
     <ul>
     {questionTwo.map(two => <li>{two}</li>)}
     </ul>
   </>)
}
```
The `return()` brackets allows you to spread you code in multiple lines. `<></>` or `<Fragment></Fragment>` both allows you to have more than one 
HTML element like `<h1>` tags or `<li>` elements inside the return statement. Now the curly braces `{}` with this you can render this list dynamically 

## Just A List Components

2 question list and mapping them into this function called `function Events()`

I have Created Arrow Message to map `questionOne.map((one) => <li key={one}>{one}</li>)`.
Keep In mind the `questionOne.map` is mapping from the questionOne which can be call an array or a list.
```js
const Message = () => {
  return questionOne.map((one) => <li key={one}>{one}</li>);
};
```

And Returning `<ol className="list-group">{Message()}</ol>` the arrow Message() in the function Events()
```js
const questionOne = [
  "Numbers are given away then data is available.",
  "Grouping is often done in groups of eight bits.",
  "Colors can be numbers in grouping graphics.",
];

const Message = () => {
  return questionOne.map((one) => <li key={one}>{one}</li>);
};

function Events() {
  const questionTwo = [
    "Communication between hardware and software.",
    "Video editing and movies.",
    "Input, processing, storage, and output.",
  ];

  let two = questionTwo.map((two) => <li key={two}>{two}</li>);
  two = [];

  return (
    <>
      <div>
        <h5>Why is all data stored in a computer in binary form?</h5>
        <ol className="list-group">{Message()}</ol>
        <br />
        <h5>What are the four primary functions of hardware?</h5>
        {two.length === 0 ? <h5>Empty Question List</h5> : null}
        <ol className="list-group">{two}</ol>
      </div>
    </>
  );
}

export default Events;
```

# Added An Onclick={} event 
`onClick={() => console.log(one)` Logging to console to see the items in list 

```js
const Message = () => {
   return questionOne.map((one) => (
      <li className="list-group-item" key={one} onClick={() => console.log(one)}>
         {one}
      </li>
   ));
};
```

# Added Index 
Put an index beside `(two, index)` and added to `console.log(two, index)` shows numbered index 
```js
let two = questionTwo.map((two, index) => (
      <li className="list-group-item" key={two} onClick={() => console.log(two, index)}>
         {two}
      </li>
   ));
```

# Added Handle (event MouseEvent)

`const handle = (event: MouseEvent) => console.log(event)` Having this event log to console and this is inside the `function Events()`
Keep in mind theres 2 lists one inside this function local and one outside global  

```js

function Events() {
   const questionTwo = [
      "Communication between hardware and software.",
      "Video editing and movies.",
      "Input, processing, storage, and output.",
   ];

  const handle = (event: MouseEvent) => console.log(event)

   let two = questionTwo.map((two, index) => (
      <li className="list-group-item" key={two} onClick={handle}>
         {two}
      </li>
   ));

   return (
      <>
         <div>
            <h5>Why is all data stored in a computer in binary form?</h5>
            <ol className="list-group">{Message()}</ol>
            <br />
            <h5>What are the four primary functions of hardware?</h5>
            {two.length === 0 && <h5>Empty Question List</h5>}
            <ol className="list-group">{two}</ol>
         </div>
      </>
   );
}

export default Events;
```

# Added An Active component 
This make all the items in this list blue. This className `className="list-group-item active"` is an active component 
```js
  <li className="list-group-item active" key={two} onClick={handle}>
         {two}
      </li>
```


# Removed const handle 
Remove the handle and put in `let selectedIndex = 0`, then added it to `<li className={selectedIndex === index ? "list-group-item active" : "list-group-item"}`
```js
  let selectedIndex = 0

   let two = questionTwo.map((two, index) => (
      <li className={selectedIndex === index ? "list-group-item active" : "list-group-item"}
         key={two} onClick={() => { selectedIndex === index }}>
         {two}
      </li>
   ));
```

# useState Hook
I have added a `const [selectedIndex, setIndex] = useState(-1)` like a hook this is used when changes are being made like clicking. And changed the `onClick={() => { setIndex(index) }}` event to `setIndex(index)`.

Now this `<li className={selectedIndex === index ? "list-group-item active" : "list-group-item"}` is new to me using an if statement inside css className its wried to me. But it works. And you can select each item in the list when clicked on.
```js
import { useState } from "react";

  const [selectedIndex, setIndex] = useState(-1)

   let two = questionTwo.map((two, index) => (
      <li className={selectedIndex === index ? "list-group-item active" : "list-group-item"}
         key={two} onClick={() => { setIndex(index) }}>
         {two}
      </li>
   ));
```


# List Written in full
This will tell react that your code will change over time, `import { useState } from "react";`. Now `questionOne[]` dose not have a `{useState}` hook i only put it on the `questionTwo[]` list. 
```js
import { useState } from "react";

const questionOne = [
   "Numbers are given away then data is available.",
   "Grouping is often done in groups of eight bits.",
   "Colors can be numbers in grouping graphics.",
];

const Message = () => {
   return questionOne.map((one) => (
      <li className="list-group-item" key={one} onClick={() => console.log(one)}>
         {one}
      </li>
   ));
};

function Events() {
   const questionTwo = [
      "Communication between hardware and software.",
      "Video editing and movies.",
      "Input, processing, storage, and output.",
   ];

   // hook
   const [selectedIndex, setIndex] = useState(-1)

   let two = questionTwo.map((two, index) => (
      <li className={selectedIndex === index ? "list-group-item active" : "list-group-item"}
         key={two} onClick={() => { setIndex(index) }}>
         {two}
      </li>
   ));

   return (
      <>
         <div>
            <h5>Why is all data stored in a computer in binary form?</h5>
            <ol className="list-group">{Message()}</ol>
            <br />
            <h5>What are the four primary functions of hardware?</h5>
            {two.length === 0 && <h5>Empty Question List</h5>}
            <ol className="list-group">{two}</ol>
         </div>
      </>
   );
}

export default Events;
```
