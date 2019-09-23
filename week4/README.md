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

I learned about the `useEffect` hook. It's an effect hook that replaces the `componentDidMount` & `shouldComponentUpdate` lifecycle methods in class components. This hook takes care of side effects, like API calls etc. Here's a very familiar scenario with classes

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
});
```

The `useEffect` in this example takes a function as argument. This function runs on every re-render. It can also take a second parameter; an array containing values we want to observe across re-renders. We call `setPosts` to modify the state inside the `useEffect` function.

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

## Day 27

## What I worked on

Cleaned up a few React experiment repositories, also read [Complete guide to useEffect](https://overreacted.io/a-complete-guide-to-useeffect/)

## A few challenges

Found it a little difficult to understand the material

## What I learned

React hooks require a different thinking from the way of thinking about state. Still a lot to learn about Hooks.

## Day 28

### What I worked on

Continued working on the blog. Github repo [here](https://github.com/vickOnRails/night-blog) and a WIP live demo [here](https://night-blog.netlify.com/)

### A few challenges

I thought I could simply lazy load the post images by storing a `loaded` boolean variable in state and rendering a placeholder image or a real one based on the value. I tried this approach

```js
const [loaded, setLoaded] = useState(false);

axios.get(URL).then(res => {
  setLoaded(res.data);
});
```

In the `post.tsx`

```js
<article className="article">
  <div className="article__image">
    <Link to={link} className="article__image_link">
      <img
        //The thumbnail variable contains a url to the original image
        //Placeholder points to a temporary image
        //I render either thumnailUrl or Placeholder based on the loaded variable
        src={loaded ? thumbnailUrl : Placeholder}
        alt="Some title for the logo"
        className="article__img"
      />
    </Link>
  </div>
  <h2 className="article__title">
    <Link to={link}>{title}</Link>
  </h2>
  <p className="article__excerpt">{body.substr(0, 100) + ` ...`}</p>
  <PostFooter />
</article>
```

I assumed this would work, but it doesn't. From what I've found, the axios `promise` returns when the JSON data is downloaded. My JSON just links to a CDN hosting the images. So when the fetch promise is resolved, and `setLoaded` updates the state, everything including the main image gets downloaded at once. This is driving crazy at the moment.

But I thought of another approach. I could possibly render all the posts with the placeholder image when the JSON data arrives. Then on the `load` event (fires when everything on the page has loaded), I could then replace the image `src` with the original ones on the JSON data.

I'll look into that tomorrow

### What I learned

`DOMContentLoaded` event fires when the HTML (Markup has loaded) while `load` fires when everything on the page has loaded: images, fonts, etc. They both fire on the `window` document.

---
