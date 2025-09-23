The **`Node`** interface is simply used to represent a node in the DOM tree.
![[Pasted image 20250118232444.png]]

Now, let's talk about the methods of the `Node` interface:

![[Screenshot 2025-01-18 at 11.26.12 PM.png]]

#### What is a `NodeList`?
A **`NodeList`** object is very similar to an `Array` object.

It supports the usage of bracket notation to access individual items, and has a `length` property containing the total number of items.

For instance, if `nodeList` is a `NodeList` instance, then we could do something such as `nodeList[0]` to access to first item of the list, and similarly `nodeList.length` to determine the total number of items in it.

However, it's very important to note that a `NodeList` is NOT the same thing as an `Array`.

A `NodeList` instance doesn't have access to any array methods, such as `indexOf()`, `push()`, `slice()`, etc, simply because it's neither an array itself, nor does it inherit from the `Array` interface.

## Factory methods to create nodes

### `createElement()`

The **`createElement()`** method, available on the `document` object, creates a given element node.

### `createDocumentFragment()`

The **`createDocumentFragment()`** factory method of the `Document` interface, as the name suggests, creates a document fragment node.

### `createTextNode()`

Although, it's not used very much in the context of HTML documents, we can also add textual content to a document by creating text nodes manually and then appending them within element nodes.

In this regard, we have at our dispense the method **`createTextNode()`** on the `Document` interface.

## Adding Nodes
### `appendChild()`

The **`appendChild()`** method of the `Node` interface adds a given node inside the calling node, as its last child.

The reason it's called _'appendChild'_ is because it adds a given node at the _end_ of the children of the calling node (i.e. the one that invoked `appendChild()`), which means that it becomes a _child_ node of the calling node.

```js
node.appendChild(childNode)
```

### `insertBefore()`

**`insertBefore()`** is yet another method to add a given node to the document. Like its name, it's slightly different than `appendChild()`.

```js
node.insertBefore(newNode, childNode)
```


## Cloning nodes

```js
node.cloneNode([deepClone])
```

The optional Boolean _`deepClone`_ argument specifies whether or not deep cloning is desired, i.e. cloning the entire subtree following from _`node`_ (including its children, and the children of these children, and so on).