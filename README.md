# 💰 React Treasure Hunt Game

As a developer, you are tasked with creating a treasure hunt game. The user will see a game board on the page and be able to select various squares on the board. Hidden behind one square is a treasure that will win the game and hidden behind another square is a bomb that will lose the game. All other squares will reveal a neutral image. The user will be given a particular number of clicks to find the treasure that will win the game.

### 🤔 Remember

- Pseudocode!!
- Ask clarifying questions

### 📚 User Stories

### Layout
- App.js: logic (container) - maintain all the data, variables, functions to pass to other components
- Square.js: display (presentational) - shows how to send the component back to the user interface
- use console.log() or reference data to display on user interface

- As a user, I can see a page with a three by three grid board game with a question mark in each square.
  - branch: board
  - known: 9 question marks and a square
  - return: 3X3 grid with question marks
  - process:
      - iterate across the values in the array and return a square using .map()
      - reference the value to make the question mark appear
```js
// App.js
import React, { useState } from "react"
import "./App.css"
import Square from "./components/Square"

const App = () => {
  const [board, setBoard] = useState([
    "?",
    "?",
    "?",
    "?",
    "?",
    "?",
    "?",
    "?",
    "?"
  ])

  return (
    <>
      <h1>Treasure Hunt Game</h1>
      {board.map((value, index)=>{
        return <Square key={index} value={value}/>
      })}
      
    </>
  )
}

export default App

// Square.js
import React from "react"

const Square = (props) => {
  console.log(props)
  return (
    <>
      <div className="square">
        {props.value}
      </div>
    </>
  )
}
export default Square
```
  - pass board as a prop and place .map() on Square.js
  ```js
    {props.board.map((value, index)=> {
        return(
          <div className="square" key={index}>
            {value}
          </div>
        )
      })} 
  ```
  - added styling to center the grid
  ```css
    #grid {
      display: flex;
      flex-wrap: wrap;
      width: 620px;
      margin: 0 auto;
    }
  ```

- As a user, when I click on one of the question marks an alert appears with the index position of that question mark in the array.
  - known: 
  - function: creates an alert message with id
    - pseudocode:
      input: index of the selected square, `selectedIndex`
      output: alert message
      name: handleClick
    - function call: onClick attribute on the specific square
  - to prevent the function from being immediately invoked, use anonymous to allow the function to be called after clicking a square
  `onClick={() => {props.handleClick(index)}}`

- As a user, when I click on one of the question marks instead of the alert the question mark turns into a tree emoji.
- As a user, if I select the winning square the question mark will become a treasure emoji and if I select the losing square the question mark will become a bomb emoji.
- As a user, I can click on a “Play Again” button that will restart the game.
- As a user, I can see a counter that shows how many guesses I have left. The counter starts at five and decrements one every time I click on a square that is not the treasure nor the bomb.
- As a user, I can see a message informing me that I won the game if I select the square that contains the treasure.
- As a user, I can see a message informing me that I lost the game if I select the square that contains the bomb.
- As a user, I cannot continue to play the game after I win or lose.
- As a user, I can see a message informing me that I lost the game when I run out of turns (the counter reaches zero).

### 🏔 Stretch Goals

- Consider how to handle a situation where the bomb and the treasure are at the same index.

### 👩‍💻 Developer Stretch Goals

- As a developer, I have a well commented application.
- As a developer, I have well written README file with instructions on how to access my repository.
- As a developer, my variables are all named semantically.
- As a developer, I have refactored and efficient code.
- As a developer, I have my application [deployed as a live website](https://render.com/docs/deploy-create-react-app).