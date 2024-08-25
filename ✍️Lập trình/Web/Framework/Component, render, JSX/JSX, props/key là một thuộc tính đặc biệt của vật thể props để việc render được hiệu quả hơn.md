---
share: true
created: 2023-10-30T14:29
updated: 2024-08-18T15:05
---
In Preact, I want to display an object:

```javascript
export default function Component() {
  const obj = { a: 'a', b: 'b'} 
  const elements = [];
  for (const [key, value] of Object.entries(obj)) {
    elements.push(<>{key}: {value}<br></br></>)
  }
  return (
    <article>
      {elements}
    </article>
  );
}
```

This returns fine:

```
a: a
b: b
```

However, if I extract the element into a separate JSX element like this:

```javascript
function Element({ key, value }) {
  return (<>{key}: {value}<br></br></>);
}
export default function Component() {
  const obj = { a: 'a', b: 'b'} 
  const elements = [];
  for (const [key, value] of Object.entries(obj)) {
    // elements.push(<>{key}: {value}<br></br></>)
    elements.push(<Element key={key} value={value} />)
  }
  return (
    <article>
      {elements}
    </article>
  );
}
```

Then the keys all become undefined:

```
: a
: b
```

It is because `key` is a special prop in (p)react, used by the framework as a hint for how to rearrange elements safely and efficiently. You'll need to use another prop.

Take the following example as a result from a component rendering.

| First Render                                                                   | Second Render                                                    |
| ------------------------------------------------------------------------------ | ---------------------------------------------------------------- |
| ```<br><article>  <div>a</div>  <div>b</div>  <div>c</div></article><br>``` | ```<br><article>  <div>a</div>  <div>c</div></article><br>``` |

The problem here is that it's unclear what has been done:

- a) has the second item been removed, or
- b) has the third item been removed, and the text of the second item changed?

(p)react could only guess, which is why we use keys.

| First Render                                                                                           | Second Render                                                                    |
| ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| ```<br><article>  <div key="a">a</div>  <div key="b">b</div>  <div key="c">c</div></article><br>``` | ```<br><article>  <div key="a">a</div>  <div key="c">c</div></article><br>``` |

With keys, (p)react is able to correctly and quickly update the list, as it knows exactly what's happened (b was removed).

Preact's tutorial has an entire section on keys, if you wanted to learn more: [https://preactjs.com/tutorial/08-keys](https://preactjs.com/tutorial/08-keys)

Nguồn:: [Why do object keys become undefined if they are accessed via an JSX element?](https://stackoverflow.com/a/78466472/3416774)

[[Props là đối số đầu tiên của hàm component, dùng để truyền giá trị các thuộc tính của nó]]