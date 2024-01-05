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

```javascript
.App{
	background-color: blue;
}
```

Note: App not app. all elements must have a closing tag.

## What is JSX_ Creating Components in React.mp4
## React Props Explained.mp4
## Rendering a List of Components.mp4
## This Is How You Handle Events In A React App.mp4
## useState.mp4
## React State Array of Objects.mp4
## useReducer.mp4
## Conditional Rendering Components in React.mp4
## useEffect Everything You Need To Know.mp4
## Fetching and Posting Data in React.mp4
## React Proxy _ Easiest Fix to CORS Errors.mp4
## Build a web app with React, Express, Mysql, S3, Heroku _ Live Lesson Demo.mp4
## Deploy React App to S3 with Custom Domain.mp4
