<a name="module_x5engine.imTip"></a>
## x5engine.imTip
Manage the JS tooltip. You can load both text and HTML inside it.

<a name="module_x5engine.imTip.Show"></a>
### .Show(obj, settings) ⇒ <code>void</code>
Show the WSX5 tooltip using the provided settings.

**Kind**: static method of <code>[x5engine.imTip](#module_x5engine.imTip)</code>  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>jQuery</code> | The object used as ToolTip anchor |
| settings | <code>object</code> | The settings passed to `Show()` |
| settings.classes | <code>string</code> | Classes to add to the tooltip container, separated by whitespace |
| settings.position | <code>string</code> | Position relative to the anchor: `top`, `bottom`, `left`, `right`, `top-left`, `top-right`, `bottom-left`, or `bottom-right` |
| settings.effect | <code>string</code> | Effect used to show the tooltip: `fade`, `bounce`, or `none` |
| settings.showTail | <code>boolean</code> | `true` to show the tooltip tail |
| settings.arrow | <code>boolean</code> | `true` to show the arrow |
| settings.hideOnFocus | <code>boolean</code> | Hide the tooltip when the anchor receives focus |
| settings.hideOnBlur | <code>boolean</code> | Hide the tooltip when the anchor loses focus |
| settings.persistant | <code>boolean</code> | Keep the tooltip visible. The historical spelling `persistant` is part of the API |
| settings.unique | <code>boolean</code> | Close other tooltips before showing this one |
| settings.text | <code>string</code> | The tooltip content. May contain HTML |
| settings.width | <code>number</code> | The tooltip width in pixels |

Arrow dimensions and graphical offsets are internal theme settings; they are not properties accepted by `Show()`.
