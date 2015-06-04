<a name="module_x5engine.boot"></a>
## x5engine.boot
Manage the bootup queue.

<a name="module_x5engine.boot.push"></a>
### .push(fName, force, priority) ⇒ <code>void</code>
Add an element to the callback queue. The added element will be called as soon as the WSX5's JS engine is ready.

**Kind**: static method of <code>[x5engine.boot](#module_x5engine.boot)</code>  

| Param | Type | Description |
| --- | --- | --- |
| fName | <code>function</code> &#124; <code>string</code> | The callback or function name to execute |
| force | <code>boolean</code> | True to add this element more than once if it's already set |
| priority | <code>number</code> &#124; <code>string</code> | The priority from 0 (most important) to an infinite number (default 5). You can also define "first" and "last" |

**Example**  
```js
// Simple loading
```