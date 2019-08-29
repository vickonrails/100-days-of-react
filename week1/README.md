## Day 1

### What I worked on
I worked on the exercises from Traversy's [TypeScript's crash course](https://www.youtube.com/watch?v=rAy_3SIqT-E) as the project I'm working on heavily requires TypeScript for Typing React.

See TypeScript tutorial [here](https://www.youtube.com/watch?v=rAy_3SIqT-E)

### A few challenges
I used `let` to declare variables in TypeScript, but it kept on giving me errors about block scope. The transpiled `.js` file converted those declarations to `var`. I had no idea why. 

While working on a little todo app, I had serious issues with deciding which components should be stateful or functional. I guess this will improve over time.

### What I learned

These are some jottings from the tutorial. 

TypeScript gives us `Strings`, `Number`, `Boolean`, `Array`, `Any`, `Void`, `Null`, `Tuple`, `Enum`, `Generics`.

- **Any**: Can be any type
- **Void**: No type returned
- **Tuple**: Array with fixed number of elements
- **Enum**: Enumerated values
- **Generics**: Constraints for some types

Typescript gives us `class based objects`, `properties`, `methods`, `encapsulation`, `Inheritance`, `access modifiers`.

Typescript files need to be transpiled into .js files. We need TSC to transpile .ts to .js.

We need Nodejs to run typescript.
To create a variable with type, we do 

```js
const myString: string;
```

We can also declare arrays too like this

```js
var strArray: string[];
```

Another way to decalre array is 

```js
const strArray: Array<string>;
```

Tuples are arrays with multiple types. We declare tuples as

```js
const mytup: [string, number];
```

When giving values to the arrays, the format must match the declared one. In the above case, the first value must be a string and the second must be a number. 

The null type can be assigned to `null`, or `undefined`. If assigned to something else, it trows an error.

#### Functions
Typescript can be used to put limits on types that functions work with. Here's how it works

```js
function getSum(num1: number, num2: number): number {}
```

The `:number` at the end of the function arguments ensures the function returns a number. If is doesn't we get an error.

We can also declare array arguments as optional by adding `?` like so

```js
function getName(firstname: string, lastname?: string) {}
```

This tells the parser that argument 2 is optional.

We can make a function return void. It will return nothing and the parser will raise an error if it returns any value. 

Interfaces can be used to create custom types

#### Classes in TypeScript

Classes can have a constructor that runs everytime an instance of that class is made. 

We can also make use of access modifiers. `Private`, `Public`, `Protected` etc.

`Private` means the variable cannot be accessed outside the class definition.

`Public` means we can access the variable from any where in the program.

`Protected` means we can only access the class from the definition and other classes that inherit the class.
We can also have methods that perform certain operations on the class properties. Methods are can also be controlled by access modifiers. 

#### Class inheritance

If a class inherits another, the constructor will take the original arguments of the new class alongside the arguments of the extended class. Classes that extend other classes must call the super() method with the arguments of the extended class.

To call a method of the extended class, we use `super.methodName()`.

Classes can also implement Interfaces. This means the interface is declared as a custom type for the class.

```js
interface UserInterface {
    name: string;
    email: string;
    register();
    payInvoice();
}


Class User implements UserInterface {}
```

- Methods of classes can also be defined in interfaces.

---

## Day 2

### What I worked on
A todo App🙈. Will share a link tomorrow

### Challenges 
I spent a lot of time with React-specific Typescript event types. I knew nothing of them before now. 

Here's the issue...
If I write normal React code as so

```js
// other boilerplate react code

handleChange = (event) => {
    this.setState({
        value: event.target.value
    })
}


<Input type="text" value={this.state.value} onChange={this.handleChange}/>

// other boilerplate react code
```

This gives an error because the type of `event` on the `handleChange` function isn't provided. TypeScript wants to be sure about the type of event passed. Here's how I solved it...

### What I learned
The browser (JavaScript) engine gives us basic events. We can get them by running `event.type`. React extends those events and puts them in the `React.syntheticEvent` variable. TypeScript wants us to provide the type of the `event` provided to us by React.

For the Input element of my todoList, I made use of the `React.changeEvent<HTMLInputElement>` which gives us the appropraite type for the Input change event. 

For the form element, I provided a `React.FormEvent<HTMLFormElement>` which is most appropraite for `form` elements. 

My errors then disappear when I update the code like so

```js
handleChange = (event:React.changeEvent<HTMLInputElement>) => {
    this.setState({
        value: event.target.value
    })
}


<Input type="text" value={this.state.value} onChange={this.handleChange}/>
```

This also applies to forms.
```js

submitForm = (event:FormEvent<HTMLFormElement>) => {
    {handler body}
}

<form onSubmit={this.submitForm}>
    {form Body}
</form>
```

Have a great day and checkout [day 1](https://github.com/vickOnRails/100-days-of-react/tree/master/week1#day-1). 

**useful links**
- [Typesafe Event Emitter](https://basarat.gitbooks.io/typescript/docs/tips/typed-event.html)

- [TypeScript and React: Events](https://fettblog.eu/typescript-react/events/)

## Day 3

### What I worked on
Unfinished Pokemon App 🙇‍ following [this tutorials](https://www.youtube.com/watch?v=0_C2X1yRRac) and [Burger builder](https://github.com/vickOnRails/Burger-App) app following [this course](https://www.udemy.com/react-the-complete-guide-incl-redux/).

### Challenges 
I was trying to use `refs` to declaratively find an element in the DOM. Plus Typescript kept frustrating me with event types. I wish there was a place where I could find all HTML related TypeScript events. 

### Learnings
I also learned about controlled and uncontrolled elements. Controlled React components have their state managed by React while uncontrolled components have their state controlled by the DOM.

A typical example is an `input` element. The React docs recommends that all form elements be controlled by React. So it's conventional to see people manage `input` value in state. We make the `input` element controlled by doing this. On the other hand, we could just let the DOM handle the state of the `input` like it does in vanilla HTML/JS. This then makes the component uncontrolled and we wouldn't need to store the `input` value in the state. 

Here's how to identify an element with refs. Refs are more suitable for class components 

```js
class App extends Component {

constructor(props){
  super(props);
  state = {}
  const inputRef = React.createRef();
  }
}

render(){
  return (
  <input ref={this.inputRef}/>
 )
}

```

More about controlled components [here](https://reactjs.org/docs/uncontrolled-components.html)

I also learned about routing with React Router and I'll try to do a little demo app with it tomorrow. 
Have a great day and checkout [day 2](https://github.com/vickOnRails/100-days-of-react/tree/master/week1#day-2). 

## Day 4

## What I worked on
I made a very [little app](https://github.com/vickOnRails/purple-blog) that fetched posts from the [jsonplaceholder](https://jsonplaceholder.typicode.com) API. I called it [purple-blog](https://purple-blog.netlify.com/). You can take a look at the source code [here](). Funny name, but got the job done.

It's built with React & Typescript.

## What Challenges I faced
Deploying to netlify was tricky. 
I have a couple of static sites hosted on netlify, but this was my first react app. I struggled to properlyy configure my `netlify.toml`file. 

I also spent 10 mins trying to find an error because I installed `@types/react-router-dom` without installing `react-router-dom`🤣🤣🤣.

## What I learned
- I learned to properly configure my `netlify.toml` file so Netlify could build the files correctly and most importantly, locate my `/build` folders containing my static `HTML` and other files.

- I finally understood how `.gitignore` files work. You basically put the path to the folders you don't want to commit, and `git` ignores them. 

- Typescript trows an error when you save a file without exporting something. It will give the following error. 


**All files must be modules when the '--isolatedModules' flag is provided.**


I tried turning the `isolatedModules` flag off (setting it to false), but Typescript trew another about `true`  being the recommended option. 

- Everything worked immediately I created empty functional components that exported nothing. 

- Also learned that by type safing our state like so, we ensure we don't mutate it directly

```js
interface IState {
    ...
}

state: ReadOnly<IState> = {}
```

I also learned CRA has native support for CSS modules and we can use them by naming them like so `Component.modules.css`.

We can then import them and use them to style components like so

```js
//Every other import
import classes from './Component.module.css';

//use them in the component
<Input className={classes.Input}/>
```
This is assuming we have `.Input` as a CSS selector.
Have a great day and checkout [day 3](https://github.com/vickOnRails/100-days-of-react/tree/master/week1#day-3). 