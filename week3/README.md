## Day 15

### What I worked on

Continued to make [one-million-africa](https://one-million-africa.netlify.com) responsive on mobile.

### A few challenges

I came across a typescript bug today, but I didn't get enough time to fix it. I hope to do so tomorrow.

### What I learned

While working with React Router, I needed to push the top `Route's` props to another `Route` component. Something like this...

```js
<Route to="/" component={Home} prop={props} />
```

But this didn't work. After a few minutes of googling, I found this detailed [article](https://tylermcginnis.com/react-router-pass-props-to-components/) on how to correctly pass props to `Route` componenets by Tyler Mcginnis.

According to the article, we could pass props to a `Route's` child by replacing the `component` attrubute with a `render` attribute like so...

```js
    <Route to="/" render={}/>
```

The `render` attribute will have to return a component that carries the props.

```js
    <Route to="/" render={(props)=><Component {...props} attr={value}>}/>
```

This way, we can pass data to `Route` children without losing our souls.

Have a great day and checkout [day 14](https://github.com/vickOnRails/100-days-of-react/tree/master/week2#day-14).

## Day 16

### What I worked on

I read some part of the Advanced React Docs.

### A few challenges

No challenge today. Except still struggling to find time for the exercise.

### What I learned

Learned more about forwarding `refs` today. See more at [link](https://reactjs.org/docs/forwarding-refs.html)
