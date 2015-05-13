<a name="module_x5engine.imTip"></a>
## x5engine.imTip
Manage the JS tooltip. You can load both text and HTML inside it.

<a name="module_x5engine.imTip.Show"></a>
### .Show(obj, json) ⇒ <code>void</code>
Show the WSX5 tooltip using the provided settings.

**Kind**: static method of <code>[x5engine.imTip](#module_x5engine.imTip)</code>  

| Param | Type | Description |
| --- | --- | --- |
| obj | <code>jQuery</code> | The object used as ToolTip anchor |
| json | <code>object</code> | The settings |
| json.classes | <code>string</code> | Classes to add to the ToolTip container separated by a white space |
| json.position | <code>string</code> | The position of the tip relative to the anchor. Must be one of the following: top, bottom, left or right. |
| json.effect | <code>string</code> | The effect used to show the tip. Must be one of the following: fade, bounce, none |
| json.showTail | <code>boolean</code> | True to show the ToolTipìs tail |
| json.text | <code>string</code> | The ToolTip's content. May contain HTML. |
| json.width | <code>Number</code> | The ToolTip's width in px. |

