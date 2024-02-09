# React Notes

## Setting up the app

```
npm create vite@latest
```

## Creating components in .jsx file

In App.jsx

```javascript
import "./App.css"
import  Component  from "./Component"

function RandomImage(){
	return <img src="link" alt="random image" />
}

function App() {

	const now = new Date().toString()

	return (
		<div className="App">
			<h1>Hello World</h1>	
			<p>My name is computer</p>
			<p>{now}</p>
			<img src"link" alt="hello" />
			
			<RandomImage />
		</div>
	)
}

export default App
```

In Component.jsx

```javascript
export default Component() {
	return <h1>Hello World</h1>
}
```

In App.css

```css
.App{
	background-color: blue;
}
```

Note: App not app. all elements must have a closing tag.

## What is JSX_ Creating Components in React.mp4

In App.jsx

```javascript
import "./App.css"

function RandomImage() {
	return <img src="https://picsum.photos/200/300" alt="random" />
}

function App() {

 const now = new Date().toString()

 return (
	<>
		<div className="App">
			<h1>Hello World</h1>
			<p>{6 + 9}</p>
			<p>{now}</p>	
		</div>
		<p>Some more text</p>

		<RandomImage />
		<RandomImage />
		<RandomImage />
	</>
 )
}
```
Component in external file(RandomImage.jsx)

```javascript
export default function RandomImage() {
	return <img src="https://picsum.photos/200/300" alt="random" />
}
```

Importing the component

```javascript
import "./App.css"
import 	RandomImage from "./RandomImage.jsx"


function App() {

 const now = new Date().toString()

 return (
	<>
		<div className="App">
			<h1>Hello World</h1>
			<p>{6 + 9}</p>
			<p>{now}</p>	
		</div>
		<p>Some more text</p>

		<RandomImage />
		<RandomImage />
		<RandomImage />
	</>
 )
}
```

## React Props Explained.mp4

Props: for when you want to use the same component more than once but change the data of the component.It's how we pass a component data. 

For Example:

App.jsx file

```python
import "./App.css"
import Joke from "./Joke.jsx"

function App(){

	const dadJoke2 = {
		joke: "I'm afraid for calendar. Its days are numberd.",
		rating: 4
	}
	
	return (
		<div>
			<h1>Dad Jokes</h1>
			
			<Joke rating={3} joke="I used to be a banker, but then I lost interest!" />
			<Joke joke={dadJoke2.joke} rating={dadJOke2.rating} />
			<Joke {...dadJoke2} />
		</div>
	)
}
```

The component

```javascript
export default function Joke(props){

	return (
		<div>
			<p>{props.joke}</p>
			<p>{props.rating}</p>
		</div>
	)
}

// OR

//export default function Joke({ rating, joke}){
//
//	return (
//		<div>
//			<p>{joke}</p>
//			<p>{rating}</p>
//		</div>
//	)
//}
```

## Rendering a List of Components.mp4

```javascript
import "./App.css"
import Joke from "./Joke.jsx"

function App(){

	jokes = [
		{
			id: 1,
			joke: "I'm afraid for calendar. Its days are numberd.",
			rating: 4
		},
		{
			id: 2,
			joke: "I'm afraid for calendar. Its days are numberd.",
			rating: 4
		},
		{
			id: 3,
			joke: "I'm afraid for calendar. Its days are numberd.",
			rating: 4
		},
		{
			id: 4,
			joke: "I'm afraid for calendar. Its days are numberd.",
			rating: 4
		},
		{
			id: 5,
			joke: "I'm afraid for calendar. Its days are numberd.",
			rating: 4
		},
	]

	jokeComponents = jokes.filter(joke => joke.rating > 3).map(joke => (
		<Joke key={joke.id} joke={joke.joke} rating={joke.rating} />
	))
	
	return (
		<div>
			<h1>Dad Jokes</h1>
			
			{jokeComponents}
		</div>
	)
}
```

## This Is How You Handle Events In A React App.mp4

```javascript
import "./App.jsx"

function App() {
	function handleClick(){
		console.log("Button Clicked")
	}
	
	function handleSubmit(e) {
		e.preventDefault()
		console.log("Form submitted")
	}

	function handleTextChange(e) {
		console.log(e.target.value)
	}

	return (
		<div className="App">
			<button onClick={handleClick}>Do Something</button>

			<form onSubmit={handleSubmit}>
				<input type="text" oneChange={handleTextChange} />
				<button type="submit">Submit</button>
			</form>
		</div>
	)
}
```

Passing event handling function to custom component

```javascript
import "./App.jsx"

import Form from "./Form.jsx"

function App() {
	function handleClick(){
		console.log("Button Clicked")
	}
	
	function handleSubmit(e) {
		console.log("Form submitted")
	}

	function handleTextChange(e) {
		console.log(e.target.value)
	}

	return (
		<div className="App">
			<button onClick={handleClick}>Do Something</button>

			<Form onSubmit={handleSubmit} />
		</div>
	)
}
```
in Form.jsx
```javascript
export default function Form({onSubmit}) {

	function handleSubmit(e) {	
		e.preventDefault()
		onSubmit()
	}

	return (
		<form onSubmit={handleSubmit}>
			<input type="text" />
			<button type="submit">Submit</button>	
		</form>
	)
}
```

## useState.mp4

In the component file Joke.jsx. The components stores it's own likes value which it can change.

```python
import { useState } from 'react'

export default function Joke({ id, text }){

 const [ likes, setlike ] = useState(0)
 const [dislikes, setDislike] = useState(0)

 const handleLike = () => {
	setLike(likes + 1)
	console.log(`like id: ${id}, totalLikesi ${likes}`
 }

 const handleDisLike = () => {
	setDislike(likes - 1)
	console.log(`dislike id: ${id}, totalLikesi ${likes}`
 }

 return (
	<div>
		<p>{text}</p>
		<p>Likes: {likes - dislikes}</p>
		<button onClick={handleLike}>thumbUP</button>
		<button onClick={handleDisLike}>thumbDown</button>
	</div>
 )
}
```

Managing state of a form

```python
import { useState } from "react"

export default function JokeForm({ onNewJoke}){

	const [text, setText] = useState("")

	const handleSubmit = (event) => {
		event.preventDefault()
		onNewJoke(text)
		setText("")
	}

	return (
		<form onSubmit={handleSubmit}>
			<input type="text" value={text} placeholder="Enter a joke" onChange={e => setText(e.target.value)} />
			<button type="submit">Submit</button>
		</form>
	)
}
```

## React State of Array and Objects.mp4

Mannaging Arrays using state

App.jsx

```javascript
import './App.css'
import Joke from './Joke'
import JokeForm from './JokeForm'

function App() {
	// use state
	const [jokes, setJokes] = useState([
		{
			id: 1,
			text; "I'm afraid for the calendar. Its days are numbered."
		},
		{
			id: 2,
			text; "I used to be addicted to soap, but I'm clean now."	
		}
	])


	// Add new joke object
	// Create a new array with the new joke + old joke array
	const handleAddJoke = (text) => {
		setJokes([joke, ...jokes])
		console.log("New joke created")
	}

	const handleDeleteJoke = (id) =>{
		setJokes(jokes.filter(joke => joke.id !== id))
		console.log("deleted joke", id)
	}

	return (
		<div>
			<h1>Dad Jokes</h1>
		
			<JokeForm onAddJoke={handleAddJoke} />
	
			{jokes.map(joke => (
				<Joke onDelete={handleDeleteJoke} key={joke.id} id={joke.id} text={joke.text} />
			))}
		</div>
	)
}

export default App
```

Joke.jsx

```javascript
import {useState} from "react"

export default function Joke({ id, text, onDelete , onLike, onDelte}) {
	const [likes, setLikes] = useState(0)

	 const handleLike = () => {
		setLike(likes + 1)
		console.log(`like id: ${id}, totalLikesi ${likes}`
 	}

 	const handleDisLike = () => {
		setDislike(likes - 1)
		console.log(`dislike id: ${id}, totalLikesi ${likes}`
 	}

	return (
		<div>
			<p>{text}</p>
			<p>Likes: {likes}</p>
			<button onClick={handleLike}>like<button>
			<button onClick={handleDislike}>dislike<button>	
			<button onClick={() => onDelete(id)}>delete<button>
		</div>
	)
}

```

## Using Require to render images

```javascript
import React from "react";

function House() {
	return (
		<div className="App">
			<img src={require("./house.jpg")} alt="House image" />	
		</div>
	)
}
```

## useReducer.mp4

```javascript
import React, { useReducer } from "react"

const ACTIONS = {
	INCREMENT: "increment",
	DECREMENT: "decrement"
}

function reducer(state, action){
	swith(action.type){
		case ACTIONS.INCREMENT:
			return ( count: state.count + 1 )
		case ACTIONS.DECREMENT:
			return ( count: state.count - 1 )
		default:
			return state
	}
}

export default function App() {
	const [state, dispatch] = useReducer(reducer, { count: 0 })

	function increment() {
		dispatch({ type: ACTIONS.INCREMENT})
	)

	function decrement() {
		dispatch({ type: ACTIONS.DECREMENT)
	)

	return (
		<>
			<button onClick={decrement}> -</button>
			<span>{state.count}</span>
			<button onClick={increment}> -</button>
		</>
	)

}
```

## Conditional Rendering Components in React.mp4

```javascript
```

## useEffect Everything You Need To Know.mp4
## Fetching and Posting Data in React.mp4
## React Proxy _ Easiest Fix to CORS Errors.mp4
## Build a web app with React, Express, Mysql, S3, Heroku _ Live Lesson Demo.mp4
## Deploy React App to S3 with Custom Domain.mp4
