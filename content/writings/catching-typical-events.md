---
title: "Catching React Typical type events"
excerpt: Detecting when react-typical animations finish to keep track 
    of the last typed value.
date: 2020-06-25T20:10:22-05:00
code: true
draft: false
---

This is a short and to the point post.

Yesterday I was trying to use the [react-typical] library to add a typing
animation in the home page of [racegex.io].

It allows some content to "appear" to be written on real time.

But I didn't want to just update some content. I wanted to use the actual
content at whatever point in time to use it as a regular expression to match the
content of other page elements (if you see the named website, you'll get it).

I needed to know when a certain word was typed. Or when a new letter was typed.

After trying to do unfruitful things with `setInterval` and `innerText` to check
on the element's content, I went to the original [camwiegert/typical], and I saw
this:

```js {hl_lines=[3,"10-12"]}
export async function type(node, ...args) {
  for (const arg of args) {
    switch (typeof arg) {
      case "string":
        await edit(node, arg);
        break;
      case "number":
        await wait(arg);
        break;
      case "function":
        await arg(node, ...args);
        break;
      default:
        await arg;
    }
  }
}
```

Thas what did it to me. `tyoe()` handles different types of arguments
differently.

When you call type using a function as an argument, it invokes it with the same
arguments that it originally received.

## onFinish

To add a 'hook' that gets called everytime Typical finishes typing a piece of
text, pass it after such text.

```jsx
const onFinish(snippet) => {
  console.log(snippet);
}

// This results in ["...", () => {}, "...", () => {}, ...]
// You can hardcode this array, but with many strings it may
// become cumbersome
const steps = ["the prequel movies are...", "great!"].reduce(
  (acc, cur) => [...acc, cur, () => onFinish(cur)],
  []
);

return <Typical loop={Infinity} steps={steps} />;
```

`type()` will handle a `string`, and then invoke `() => onFinish()`.

[See it in action here][code-onfinish]

## onType

Now, if you want to add a custom handler after every type event, you must
"inject" the callback after every typed letter. But to avoid your letters from
being deleted you must accumulate them. And then go in reverse. Like this:

```js
[
  "t",
  handler,
  "th",
  handler,
  "the",
  handler,
  //...
  "the prequel movies are...",
  handler,
  //...
  "the",
  handler,
  "th",
  handler,
  "t",
  handler
];
```

Programmatically, we can do it like this:

```js
const text = "the prequel movies are...";

// This creates a range (0, 1, 2, 3, ... text.length)
const indexes = [...Array(text.length).keys()];

// This appends [1, 2, 3, 4] with [3, 2, 1], for example
// It's sliced to avoid duplicating the last item. ([1, 2, 3, 3, 2, 1])
// It's spreaded to avoid .reverse() from mutating the original array
[...indexes, ...[...indexes].reverse().slice(1, indexes.length)]
  // [0, 1, ..., 25, 26, 25, ..., 1, 0]
  .map((i) =>
    // This creates a substring from 0 to i, finally accomplishing
    // what we wanted
    text.substr(0, i + 1)
  );
```

We can now just wrap it in an arrow function, and mapping our original array of
texts to type!

```jsx {hl_lines=[10,11]}
const myComponent = () => {
  const [steps] = useState(
    ["the prequel movies are...", "great!"]
      .map((e) => {
        const e_i = [...Array(e.length).keys()];
        return [...e_i, ...[...e_i].reverse().slice(1, e_i.length)]
          .map((i) => e.substr(0, i + 1))
          .reduce((acc, cur) => [...acc, cur, () => onType(cur)], []);
      })
      // This is to flat the array of arrays, becase the result
      // of the previous function is an array of arrays!
      .reduce(
        (acc, cur) => [
          ...acc,
          ...cur,
          // You can pass numbers (ms) to wait after a word is typed
          1000
        ],
        []
      )
  );

  const [typeContent, setTypeContent] = useState("");
  const onType = useCallback(setTypeContent, [setTypeContent]);

  return <Typical loop={Infinity} steps={steps} />;
};
```

It may look cryptic, but it works, runs once, and it'll always work.

**Note!** This will always leave the first letter of each text being displayed.
To avoid that, prefix every text with a space. It's a quick solution, although
not the most correct one. (e.g. `[" hello", " there"]`)

[See it in action here][code-onfinish]

---

I hope this was useful for someone. I guess it'll sill be for me eventually.

[react-typical]: https://github.com/catalinmiron/react-typical
[racegex.io]: https://racegex.io
[camwiegert/typical]: https://github.com/camwiegert/typical/
[code-ontype]: https://codesandbox.io/s/react-typical-ontype-9g1p6
[code-onfinish]: https://codesandbox.io/s/react-typical-onfinish-35pkv

[^1]: blob/9a9da83b9ef1693775accd5d7b59c7a8c1be219d/typical.js#L10
