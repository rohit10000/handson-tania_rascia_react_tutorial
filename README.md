## Tania Rascia (React Tutorial: An Overview and Walkthrough)

### React prerequisites.

Basic familiarity with HTML & CSS.
Basic knowledge of JavaScript and programming.
Basic understanding of the DOM.
Familiarity with ES6 syntax and features.
Node.js and npm installed globally.

### Goal:

Learn about:
	React: the React top level API
	Babel: a JavaScript compiler that lets us use ES6+ in old browsers
	DOM: adds DOM-specific methods
	Webpack
	JSX
	components
	props
	state
	lifecycle
	
### 1. Brief on app-setup and JSX:
	
Create React App: npx create-react-app react-tutorial
	
JSX: JavaScript + XML (extensible markup language)
using JSX:
```
const heading = <h1 className="site-heading">Hello, React</h1>
```
without JSX:
```
const heading = React.createElement('h1', {className: 'site-heading'}, 'Hello, React!')
```
JSX is actually closer to JavaScript, not HTML, so there are a few key differences to note when writing it.

className is used instead of class for adding CSS classes, as class is a reserved keyword in JavaScript.
Properties and methods in JSX are camelCase - onclick will become onClick.
Self-closing tags must end in a slash - e.g. <img />

<i><b>Note:</b></i>
JavaScript expressions can also be embedded inside JSX using curly braces, including variables, functions, and properties.
```
const name = 'Tania'
const heading = <h1>Hello, {name}</h1>
```

### 2. Components
	-> class component
	eg.
	```
		class ClassComponent extends Component {
		  render() {
			return <div>Example</div>
		  }
		}
	```
	-> simple component(which is a function)
	eg.
	```
		const SimpleComponent = () => {
		  return <div>Example</div>
		}
	```
		
<i><b>Note:</b></i> A class component must include render(), and the return can only return one parent element.
	

3. Props
	eg.
	```
		const TableBody = (props) => {
		  const rows = props.characterData.map((row, index) => {
			return (
			  <tr key={index}>
				<td>{row.name}</td>
				<td>{row.job}</td>
			  </tr>
			)
		  })

		  return <tbody>{rows}</tbody>
		}
		
		class Table extends Component {
		  render() {
			const {characterData} = this.props

			return (
			  <table>
				<TableHeader />
				<TableBody characterData={characterData} />
			  </table>
			)
		  }
		}
	```
<i><b>Note:</b></i> You should always use keys when making lists in React, as they help identify each list item.

### 4. state
	You must use this.setState() to modify an array. 
	Simply applying a new value to this.state.property will not work.

Some useful example code:
```
	removeCharacter = (index) => {
	  const {characters} = this.state

	  this.setState({
		characters: characters.filter((character, i) => {
		  return i !== index
		}),
	  })
	}
	
	handleSubmit = (character) => {
	  this.setState({characters: [...this.state.characters, character]})
	}
```
### 5. Lifecycle methods:
	<a href="https://reactjs.org/docs/react-component.html">Read link: https://reactjs.org/docs/react-component.html</a>

### 6. Building and Deploying a React App to gh-pages
		- inside package.json
		- "homepage": "https://rohit10000.github.io/handson-tania_rascia_react_tutorial",
		- ``` "scripts": {
			  // ...
			  "predeploy": "npm run build",
			  "deploy": "gh-pages -d build"
			}
			```
		- npm install --save-dev gh-pages
		- npm run build
		- npm run deploy


### Some helpful links:
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax
