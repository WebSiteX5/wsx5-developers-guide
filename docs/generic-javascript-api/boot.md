<a name="module_x5engine.boot"></a>
## x5engine.boot
Manage the bootup queue.Everytime you add a callback to the queue, it will be called as soon as the x5engine is ready after page loading.It is really similar to the jQuery $(document).ready() method but with some extra features.

<a name="module_x5engine.boot.push"></a>
### .push(fName, force, priority) ⇒ <code>void</code>
Add an element to the callback queue. The added element will be called as soon as the WSX5's JS engine is ready.The callback will be called accordingly to the specified priority.

**Kind**: static method of <code>[x5engine.boot](#module_x5engine.boot)</code>  

| Param | Type | Description |
| --- | --- | --- |
| fName | <code>function</code> &#124; <code>string</code> | The callback or function name to execute |
| force | <code>boolean</code> | True to add this element more than once if it's already set |
| priority | <code>number</code> &#124; <code>string</code> | The priority from 0 (most important) to an infinite number (default 5). You can also define "first" and "last" |

**Example**  
```js
// Simple loadingx5engine.boot.push(function () { alert('Hello World!'); });// Do this firstx5engine.boot.push(function () { alert('Hello World!'); }, false, "first");
```
