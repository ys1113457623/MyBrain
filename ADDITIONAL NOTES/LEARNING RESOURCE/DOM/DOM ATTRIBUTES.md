## Getting an attribute's value

The **`getAttribute()`** method of the `Element` interface allows us to obtain the value of an arbitrary attribute defined on the calling element.

```js
element.getAttribute(name)
```

_`name`_ is the name of the attribute whose value we want to retrieve, treated case-insensitively for HTML documents. Upon success, the method returns that value.

// Note -> if the attribute is defined on the element without any value, i.e. it's a Boolean attribute, `getAttribute()` will return back an empty string (`''`) as its value.

```html
<h1 id="h1" contenteditable>A heading</h1>
```

```js
const h1Ele = document.getElementById('h1')
h1Ele.getAttribute('contenteditable') -> ''
```

## Setting an attribute
The `setAttribute()` method is used to set an attribute to a given value. If the attribute doesn't exist on the calling element, it's added.

```js
element.setAttribute(name, value)
```

## Checking for attributes

Often times rather than retrieving the value of a given attribute, we're more interested in figuring out whether or not it really even exists on a particular element.

```js
element.hasAttribute(name)
```

## Removing an attribute

The **`removeAttribute()`** method allows us to remove an attribute from an element node.

```js
element.removeAttribute(name)
```

## The `classList` property

The `classList` property returns back an instance of the **`DOMTokenList`** interface. `DOMTokenList` is a means of working with a given attribute in terms of a set of **_tokens_** which are simply strings.

![[Pasted image 20250119193619.png]]

## The `dataset` property

The `dataset` property of an element node (or precisely speaking, of the `HTMLElement` interface) allows us to work with `data-` attributes on the element. It returns back a **`DOMStringMap`** instance.

#### `DOMStringMap` is exotic!

Well, an exotic object (or interface) is one which doesn't follow the normal internal utilities of objects. The `arguments` object is an example of an exotic object.

In a normal object `obj`, when we get a property using an expression such as `obj.prop`, the value of the underlying property is returned, just as it's stored in memory (assuming that we're talking about a [data property](https://www.codeguage.com/courses/js/objects-property-attributes)).

However, in the case of a `DOMStringMap` instance `obj`, when we get a property using an expression `obj.prop`, an internal function is called that forms the return value right at the moment, by getting the value of the `data-prop` attribute from the calling element node.






