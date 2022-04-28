# Scroll Utilities

The X5 Engine API provides you a set of scroll-related utilities.

* [x5engine.utils.scroll](#module_x5engine.utils.scroll)
    * [.observe(resizeCallback, updateCallback)](#module_x5engine.utils.scroll.observe)
    * [resizeCallback](#module_x5engine.utils.scroll.resizeCallback)
    * [updateCallback](#module_x5engine.utils.scroll.updateCallback)
* [x5engine.utils.scrollHelper(element)](#module_x5engine.utils.scrollHelper)
    * [.always()](#module_x5engine.utils.scrollHelper.always)
    * [.inViewport(overflowTop, overflowBottom)](#module_x5engine.utils.scrollHelper.inViewport)
    * [.focalPoint(callback)](#module_x5engine.utils.scrollHelper.focalPoint)
    * [.objectFocalPoint(callback)](#module_x5engine.utils.scrollHelper.objectFocalPoint)
    * [.percentiageScrolled(callback)](#module_x5engine.utils.scrollHelper.percentiageScrolled)
    * [.objectPercentiageScrolled(callback)](#module_x5engine.utils.scrollHelper.objectPercentiageScrolled)

<a name="module_x5engine.utils.scroll"></a>
## x5engine.utils.scroll

Provides a set of static methods that may help in managing the scroll-related changes.

<a name="module_x5engine.utils.scroll.observe"></a>
### .observe(resizeCallback, updateCallback) ⇒ <code>void</code>

Adds a new observer. The observer will be updated thru the <code>updateCallback</code>.
The <code>resizeCallback</code> will be called immediately to get the observation rules.
The rules define how to filter updates and call <code>updateCallback</code> only when needed.

**Kind**: static method of <code>[x5engine.utils.scroll](#module_x5engine.utils.scroll)</code>

| Param          | Type                  | Description                                                              |
| -------------- | --------------------- | ------------------------------------------------------------------------ |
| resizeCallback | <code>function</code> | Called when the viewport is resized, it must return a bool or a function, il will be used to filter <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> calls                                                                                                               |
| updateCallback | <code>function</code> | Called to send the updated scroll position                               |

**Since**: 2022.1.5.1

**Example**  
```js
function resizeCallback(width, height) {
    // updateCallback will be called starting from when
    // the scroll position reaches the 50% of the page height
    return (scrollPosition) => scrollPosition > height / 2;
}
function updateCallback(scrollPosition) {
    // Update the page elements by using the scroll position...
}
x5engine.utils.scroll.observe(resizeCallback, updateCallback);
```

<a name="module_x5engine.utils.scroll.resizeCallback"></a>
### resizeCallback

Called when the viewport is resized, it must return a bool or a function, il will be used to filter <code>updateCallback</code> calls.

**Kind**: callback function for <code>[observe](#module_x5engine.utils.scroll.observe)</code> method.

| Param  | Type                | Description                    |
| ------ | ------------------- | ------------------------------ |
| width  | <code>number</code> | Current width of the viewport  |
| height | <code>number</code> | Current height of the viewport |

**Since**: 2022.1.5.1

**Returns**: <code>function</code> &#124; <code>boolean</code> - the filter function, will be called with the current scroll position to filter <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> calls; when bool is returned, it defines if the <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> must be called or not.

<a name="module_x5engine.utils.scroll.updateCallback"></a>
### updateCallback

Called when the page is scrolled.

**Kind**: callback function for <code>[observe](#module_x5engine.utils.scroll.observe)</code> method.

| Param           | Type                | Description                          |
| --------------- | ------------------- | ------------------------------------ |
| scrollPosition  | <code>number</code> | Current scroll position of the page  |

**Since**: 2022.1.5.1

<a name="module_x5engine.utils.scrollHelper"></a>
## x5engine.utils.scrollHelper(element) ⇒ <code>object</code>

Provides a set of helper methods that may be used in conjunction with the <code>[observe](#module_x5engine.utils.scroll.observe)</code> method to handle common behaviors.

**Kind**: static method

| Param    | Type                 | Description                                       |
| -------- | -------------------- | ------------------------------------------------- |
| element  | <code>Element</code> | *Optional* DOM Element to observe the scroll for  |

**Since**: 2022.1.5.1

**Returns**: <code>object</code> - An object containig different scroll helper methods

<a name="module_x5engine.utils.scrollHelper.always"></a>
### .always() ⇒ <code>function</code>

This function can be called to obtain a <code>[resizeCallback](#module_x5engine.utils.scroll.resizeCallback)</code> that always filter the observing element.

**Kind**: <code>[resizeCallback](#module_x5engine.utils.scroll.resizeCallback)</code> provider
**Since**: 2022.1.5.1
**Returns**: <code>function</code>

<a name="module_x5engine.utils.scrollHelper.inViewport"></a>
### .inViewport(overflowTop, overflowBottom) ⇒ <code>function</code>

This function can be called to obtain a <code>[resizeCallback](#module_x5engine.utils.scroll.resizeCallback)</code> that filter the observing element when it is into the viewport.

**Kind**: <code>[resizeCallback](#module_x5engine.utils.scroll.resizeCallback)</code> provider

| Param           | Type                | Description                                     |
| --------------- | ------------------- | ----------------------------------------------- |
| overflowTop     | <code>number</code> | *Optional* tolerance on top of the element     |
| overflowBottom  | <code>number</code> | *Optional* tolerance on bottom of the element  |

*If <code>overflowBottom</code> is not specified, the value of <code>overflowTop</code> will be used instead.*

**Since**: 2022.1.5.1
**Returns**: <code>function</code>

<a name="module_x5engine.utils.scrollHelper.focalPoint"></a>
### .focalPoint(callback) ⇒ <code>function</code>

This function can be called to obtain an <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> that wraps the given <code>callback</code>. The <code>callback</code> will be called with the scroll position of the center of the viewport.

**Kind**: <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> wrapper

| Param        | Type                  | Description                         |
| ------------ | --------------------- | ----------------------------------- |
| callback     | <code>function</code> | Callback function to be wrapped     |

**Since**: 2022.1.5.1
**Returns**: <code>function</code>

<a name="module_x5engine.utils.scrollHelper.objectFocalPoint"></a>
### .objectFocalPoint(callback) ⇒ <code>function</code>

This function can be called to obtain an <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> that wraps the given <code>callback</code>. The <code>callback</code> will be called with the distance between the center of the viewport and the center of the observing element.

**Kind**: <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> wrapper

| Param        | Type                  | Description                         |
| ------------ | --------------------- | ----------------------------------- |
| callback     | <code>function</code> | Callback function to be wrapped     |

**Since**: 2022.1.5.1
**Returns**: <code>function</code>

<a name="module_x5engine.utils.scrollHelper.percentiageScrolled"></a>
### .percentiageScrolled(callback) ⇒ <code>function</code>

This function can be called to obtain an <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> that wraps the given <code>callback</code>. The <code>callback</code> will be called with the percentiage of scrolled page.

**Kind**: <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> wrapper

| Param        | Type                  | Description                         |
| ------------ | --------------------- | ----------------------------------- |
| callback     | <code>function</code> | Callback function to be wrapped     |

**Since**: 2022.1.5.1
**Returns**: <code>function</code>

<a name="module_x5engine.utils.scrollHelper.objectPercentiageScrolled"></a>
### .objectPercentiageScrolled(callback) ⇒ <code>function</code>

This function can be called to obtain an <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code> that wraps the given <code>callback</code>. The <code>callback</code> will be called with the percentiage of object scrolled. The percentiage starts growning when the top of the object scrolls into the viewport and stops when the bottom of the object reaches the bottom of the viewport.

**Kind**: <code>[updateCallback](#module_x5engine.utils.scroll.updateCallback)</code>

| Param        | Type                  | Description                         |
| ------------ | --------------------- | ----------------------------------- |
| callback     | <code>function</code> | Callback function to be wrapped     |

**Since**: 2022.1.5.1
**Returns**: <code>function</code>
