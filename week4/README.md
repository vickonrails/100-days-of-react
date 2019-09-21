## Day 23

### What I worked on

Completed the little note taking app with styled components and React hooks. Demo [here](https://note-taking-styled.netlify.com/) and the github [gist](https://gist.github.com/vickOnRails/f6e6f9edb22b7688602171ed8c9f85b0).

### A few challenges

ReactJs discourages mutating the state. We create new states for our applications whenever the old one changes. React hooks are no exception too. But for some reason, it took me a few hours to make this simple thing work well.

```js
import React, { useState } from "react";
//---- other imports

//Initializing the state
const [notes, setNotes] = useState([]);

//Assuming the note variable holds the notes to be added.
const newNote = {
  title: note.value,
  content: note.value
};

// Here's how I would update the state without immutably?
setNotes(prevNotes => [...prevNotes, newNote]);
```

### What I learned

Nothing I can remember. Styled components still feel strange.
My next thing is going to be a Medium clone. I hope to learn a whole lot from it. I'd be using styled components (or maybe not), React Router & Typescript.

## Day 24

### What I worked on

Started building the Medium like clone. Will share the repo when I get things up.

### A few challenges

Typescript really hates me. Nothing else apart from that.

### What I learned

Nothing today.

---

## Day 25

### What I worked on

Continued working on the blog clone. Github repo [here](https://github.com/vickOnRails/night-blog)

### A few challenges

Nothing related to React or Typescript

### What I learned

Nothing lately. I think I've gotten the hang of things that I don't learn much new things anymore😎.

---

## Day 26

### What I worked on

Continued working on the blog clone. Github repo [here](https://github.com/vickOnRails/night-blog) and a WIP live demo [here](https://night-blog.netlify.com/)

### A few challenges

None.

### What I learned

I learned about the `useEffect` hook. It's an effect hook that replaces the `componentDidMount` & `componentWillUpdate` lifecycle methods in class components. This hook takes care of side effects, like API calls etc. Here's a very familiar scenario

```js
  componentDidMount(){
    fetch(URL)
    .then(res=>res.json())
    .then(jsonRes=>{
      this.setState(prevState=>{/* set State here */});
    })
    .catch(err => {
      throw err;
    });
  }
```

Here's how we could do the same thing with the `useEffect` hook

```js
const [posts, setPosts] = useState([]);

useEffect(() => {
  fetch(URL)
    .then(res => res.json())
    .then(jsonRes => {
      setPosts(jsonRes);
    })
    .catch(err => {
      throw err;
    });
}, [posts]);
```

The `useEffect` in this example takes a function as argument. This function runs on every re-render. It can also take a second parameter, which is an array containing values we want to observe across re-renders. We call `setPosts` to modify the state inside the `useEffect` function.

```js
const [posts, setPosts] = useState([]);

useEffect(() => {
  fetch(URL)
    .then(res => res.json())
    .then(jsonRes => {
      setPosts(jsonRes);
    })
    .catch(err => {
      throw err;
    });
}, [posts]);
```

The second argument of `useEffect` is a value from our `useState` function. We want to only execute the function (first argument) when the `post` value changes. Much like what `shouldComponentUpdate` gives us.

---
