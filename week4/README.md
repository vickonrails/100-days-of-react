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

Started building the Medium clone. Will share the repo when I get things up.

### A few challenges

Typescript really hates me. Nothing else apart from that.

### What I learned

Nothing today.
