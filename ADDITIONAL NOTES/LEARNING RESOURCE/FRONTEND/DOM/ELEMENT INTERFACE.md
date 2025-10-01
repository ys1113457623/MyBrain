It contains properties and methods that specifically apply only to elements in the DOM. Things such as children elements (not any arbitrary node), next element sibling, attributes, the inner HTML content, all apply to the `Element` interface.

## Properties
![[Pasted image 20250118235932.png]]

## Methods
![[Screenshot 2025-01-19 at 12.18.07 AM.png]]


## The `children` property
In particular, it returns back an `HTMLCollection` instance containing only those child nodes of the calling element (i.e. the element node on which the property is accessed) that are elements themselves.

## The `firstElementChild` and `lastElementChild` properties
The **`firstElementChild`** and **`lastElementChild`**, once again, are similar to the `firstChild` and `lastChild` properties of the `Node` interface, but with a slight difference.

That is, `firstElementChild` and `lastElementChild` return the first and last child node of the calling element node that is an **element itself**, respectively.

## The `previousElementSibling` and `nextElementSibling` properties

That is, `previousElementSibling` returns the previous sibling of the calling element node that is an element, or `null` if there is no preceding sibling that's an element or just about no preceding sibling at all.

## The `innerHTML` property

The **`innerHTML`** property allows us to get, as well as set, the HTML content inside a given element node.

It's defined in a separate web standard entitled [DOM Parsing and Serialization](https://w3c.github.io/DOM-Parsing/#dom-innerhtml-innerhtml).

When `innerHTML` is accessed in a _'get'_ context on a given element node, all the children nodes of the element are **_serialized_** based on the HTML serialization algorithm as specified in [Section 13.3 — Serializing HTML fragments](https://html.spec.whatwg.org/#serialising-html-fragments) of the [WHATWG HTML standard](https://html.spec.whatwg.org/).

In simpler words, the serialization algorithm is simply a means of going from an object representation of every child node, of the calling element node, to its corresponding string representation. This requires reading tag names, node values, attributes, manually concatenating angle brackets (`<` and `>`), equals sign ('='), quotes (`"`), and much more.

It's clearly not an easy task, but at the same time, not _as_ difficult as the one that happens when we set `innerHTML`.

While setting `innerHTML`, we provide the property a string containing some HTML markup to be added right inside the element. This string has to be processed and then a set of corresponding nodes to be added right inside the element.

Formally the process of going from a string representation to actual DOM nodes is referred to as **_parsing_**. The HTML parsing algorithm used can be read in [Section 13.4 — Parsing HTML fragments](https://html.spec.whatwg.org/#parsing-html-fragments) of the same HTML standard discussed above.

Parsing is a way more challenging task than serialization. It has to take into account the fact that a given HTML markup might be invalidly written, work out the nesting of elements correctly, and a lot more.

This is the reason why it's recommended to use the least amount of `innerHTML`, as possible, to set HTML content. Many web browsers do optimize `innerHTML` in many many ways, but that doesn't mean that we could carelessly use it in any way we like. _Not at all!_

It sure comes with a performance penalty if called again and again and again. We'll talk about the performance of the various ways to carry out DOM mutation later in this unit, in the chapter [HTML DOM — Performance](https://www.codeguage.com/courses/js/html-dom-performance).

## Inserting nodes

### `insertAdjacentElement()`

The `insertAdjacentElement()` method adds a given element node adjacent to the calling element.

```js
element.insertAdjacentElement(position, elementNode)
```


### `insertAdjacentText()`

The **`insertAdjacentText()`** method operates similar to the `insertAdjacentElement()` method with one obvious difference.

```js
element.insertAdjacentText(position, text)
```

### `insertAdjacentHTML()`

As with `insertAdjacentElement()` and `insertAdjacentText()`, the **`insertAdjacentHTML()`** method of the `Element` interface allows us to insert a given piece of HTML content adjacent to the calling element node.

```js
element.insertAdjacentHTML(position, html)
```