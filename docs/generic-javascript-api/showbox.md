<a name="x5engine.imShowBox"></a>
## x5engine.imShowBox(settings, [startIndex], [launcher]) ⇒ <code>bool</code>
Show the ShowBox using the provided settings.

**Kind**: global function  
**Returns**: <code>bool</code> - Always return false to let the function to be used in the "onclick" event  

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| settings | <code>object</code> |  | The settings object. For each element in it, the default value is the one set inside the ShowBox settings of WSX5. |
| settings.allowFrameTransparency | <code>boolean</code> |  | True to allow the iframes transparency in the content |
| settings.autoplay | <code>boolean</code> |  | True to automatically skip from a media to the next every autoplayTime milliseconds |
| settings.autoplayTime | <code>number</code> |  | Number of milliseconds between every media transition |
| settings.background | <code>string</code> |  | The external background color. |
| settings.borderWidth | <code>object</code> |  | The object containing the border width. |
| settings.borderWidth.top | <code>number</code> |  |  |
| settings.borderWidth.left | <code>number</code> |  |  |
| settings.borderWidth.bottom | <code>number</code> |  |  |
| settings.borderWidth.right | <code>number</code> |  |  |
| settings.borderColor | <code>string</code> |  | The border color |
| settings.borderRadius | <code>number</code> |  | The border radius |
| settings.boxColor | <code>string</code> |  | The internal background color |
| settings.buttons | <code>object</code> |  | The settings of the two buttons used to scroll the medias (one left and one right). If no setting is provided, the buttons are not shown. |
| settings.buttonRight | <code>object</code> |  | The settings of the right button |
| settings.buttonRight.url | <code>string</code> |  | Url of the image shown as right button |
| settings.buttonRight.position | <code>object</code> |  | The position of the right button expressed as x and y offset from the right ShowBox border |
| settings.buttonRight.position.x | <code>number</code> |  |  |
| settings.buttonRight.position.y | <code>number</code> |  |  |
| settings.buttonLeft | <code>object</code> |  | The settings of the left button |
| settings.buttonLeft.url | <code>string</code> |  | Url of the image shown as left button |
| settings.buttonLeft.position | <code>object</code> |  |  |
| settings.buttonLeft.position.x | <code>number</code> |  | The position of the left button expressed as x and y offset from the left ShowBox border |
| settings.buttonLeft.position.y | <code>number</code> |  |  |
| settings.closeImg | <code>string</code> |  | Url of the image used to close the ShowBox |
| settings.effect | <code>string</code> |  | The effect used to show the ShowBox. Must one of the following: "none", "fade", "move", "zoom", "hide". |
| settings.fontFamily | <code>string</code> |  | The description font family |
| settings.fontStyle | <code>string</code> |  | The description font style |
| settings.fontWeight | <code>string</code> |  | The description font weight |
| settings.fontSize | <code>string</code> |  | The description font size |
| settings.helperBg | <code>string</code> |  | Background color used for the helper image |
| settings.innerBorder | <code>number</code> |  | The internal padding size in px |
| settings.loadingImg | <code>string</code> |  | Url of the spinner image shown while the ShowBox is loading its content |
| settings.media | <code>array</code> |  | The array of settings of each media loaded in the ShowBox |
| settings.media.type | <code>string</code> |  | Must be one of the following types: image,video,sound,youtube,vimeo,html |
| settings.media.url | <code>string</code> |  | Url of the media to be loaded inside the ShowBox |
| settings.media.width | <code>number</code> |  | Width in px |
| settings.media.height | <code>number</code> |  | Height in px |
| settings.media.html | <code>number</code> |  | Code to be loaded inside the ShowBox if the specified media type is "html" |
| settings.opacity | <code>number</code> |  | The external background opacity. |
| settings.swipeImg | <code>string</code> |  | Url of the helper image shown on touch devices |
| settings.shadow | <code>string</code> |  | The ShowBox's shadow |
| settings.textColor | <code>string</code> |  | The description text color |
| settings.textAlignment | <code>string</code> |  | The description text alignment |
| [startIndex] | <code>number</code> | <code>0</code> | The index of the image to show when the ShowBox is launched |
| [launcher] | <code>DOMObject</code> | <code></code> | The DOM element used as start point when the ShowBox is shown using the "Zoom" or "Zoom and Hide" effects |

**Example**  
```js
x5engine.imShowBox({	media: [		{			url:'myimage1.jpg',			width: 800,			height: 400		},		{			url:'myimage2.jpg',			width: 800,			height: 600		}	]});
```
