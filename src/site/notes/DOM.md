---
{"type":"note","title":"DOM","alias":"Document Object Model","dg-publish":true,"created":"2021-08-30T13:51:14","modified":"2022-11-17T18:13:44","sup":[["Language","language"]],"state":"done","related":["xml","html"],"permalink":"/dom/","dgPassFrontmatter":true,"updated":"2022-11-17T18:13:44"}
---


# DOM

The Document Object Model (DOM) is a cross-platform and language-independent interface that treats an [[XML\|XML]] or [[HTML\|HTML]] document as a **tree structure** wherein each node is an object representing a part of the document.

## DOM and [[HTML\|HTML]]

When you use a web browser to request a page like `https://example.com` the server returns HTML like this:

```html
<!doctype html>
<html>
    <head>
        <title>Hello, world!</title>
    </head>
    <body>
        <h1>Hello, world!</h1>
        <p>This is a hypertext document on the World Wide Web.</p>
        <script src="/script.js" async></script>
    </body>
</html>
```

The browser parses the HTML and creates a tree of objects like this:

```text
html
  head
    title
  body
    h1
    p
    script
```

This tree of objects, or nodes, representing the page's content is called the DOM. Right now it looks the same as the HTML, but suppose that the script referenced at the bottom of the HTML runs this code:

```js
const h1 = document.querySelector('h1');
h1.parentElement.removeChild(h1);
const p = document.createElement('p');
p.textContent = 'Wildcard!';
document.body.appendChild(p);
```

That code removes the `h1` node and adds another `p` node to the DOM. The complete DOM now looks like this:

```text
html
  head
    title
  body
    p
    script
    p
```

The page's HTML is now different from its DOM. In other words, HTML represents **initial** page content, and the DOM represents **current** page content. When [[JavaScript\|JavaScript]] adds, removes, or edits nodes, the DOM becomes different than the HTML.

See [Introduction to the DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) to learn more.
