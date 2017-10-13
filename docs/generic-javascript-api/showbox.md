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
| settings.effect | <code>string</code> |  | The effect used to show the ShowBox. Must one of the following: "none", "fade", "move", "zoom", "hide". |
| settings.fontFamily | <code>string</code> |  | The description font family |
| settings.fontStyle | <code>string</code> |  | The description font style |
| settings.fontWeight | <code>string</code> |  | The description font weight |
| settings.fontSize | <code>string</code> |  | The description font size |
| settings.innerBorder | <code>number</code> |  | The internal padding size in px |
| settings.media | <code>array</code> |  | The array of settings of each media loaded in the ShowBox |
| settings.media.type | <code>string</code> |  | Must be one of the following types: image,video,sound,youtube,vimeo,html |
| settings.media.url | <code>string</code> |  | Url of the media to be loaded inside the ShowBox |
| settings.media.width | <code>number</code> |  | Width in px |
| settings.media.height | <code>number</code> |  | Height in px |
| settings.media.html | <code>number</code> |  | Code to be loaded inside the ShowBox if the specified media type is "html" |
| settings.opacity | <code>number</code> |  | The external background opacity. |
| settings.shadow | <code>string</code> |  | The ShowBox's shadow |
| settings.textColor | <code>string</code> |  | The description text color |
| settings.textAlignment | <code>string</code> |  | The description text alignment |
| [startIndex] | <code>number</code> | <code>0</code> | The index of the image to show when the ShowBox is launched |
| [launcher] | <code>DOMObject</code> |  | The DOM element used as start point when the ShowBox is shown using the "Zoom" or "Zoom and Hide" effects |

Parameters available until v13

| Param | Type | Default | Description |
| --- | --- | --- | --- |
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
| settings.helperBg | <code>string</code> |  | Background color used for the helper image |
| settings.swipeImg | <code>string</code> |  | Url of the helper image shown on touch devices |

Parameters available since v14

| Param | Type | Default | Description |
| --- | --- | --- | --- |
| settings.boxClass | <code>string</code> |  | The classname to be assigned tothe mediabox |
| settings.buttonLeft | <code>string</code> |  | HTML of the left button |
| settings.buttonRight | <code>string</code> |  | HTML of the right button |
| settings.buttonClose | <code>string</code> |  | HTML of the close button |
| settings.buttonEnterFS | <code>string</code> |  | HTML of the 'enter fullscreen' button |
| settings.buttonExitFS | <code>string</code> |  | HTML of the 'exit fullscreen' button |
| settings.buttonZoomIn | <code>string</code> |  | HTML of the zoom+ button |
| settings.buttonZoomOut | <code>string</code> |  | HTML of the zoom- button |
| settings.buttonZoomRestore | <code>string</code> |  | HTML of the 'zoom restore' button |
| settings.windowPadding | <code>number</code> |  | The size of the margin from the viewport |
| settings.showProgress | <code>boolean</code> |  | True to show the progress number on the top right corner of he screen, if more than one media is defined |
| settings.fullScreenEnabled | <code>boolean</code> |  | True to enable fullscreen, when available. If the browser doesn't support HTML5 Fullscreen API, the button will be automatically disabled |
| settings.zoomEnabled | <code>boolean</code> |  | True to enable zoom on images media. For other types of media, the button will be disabled  |
| settings.showThumbs | <code>boolean</code> |  | True to show the thumbs of the media, if more than one media is defined  |
| settings.thumbSize | <code>number</code> |  | The size of the thumbs |
| settings.transitionEffect | <code>string</code> |  | The transition effect to be applied between two media. Must one of the following: 'fade', 'horizontalSlide', 'verticalSlide', 'zoom', 'elasticFromTop', 'elasticFromBottom', 'elasticFromRight', 'elasticFromLeft', 'bounceFromTop', 'bounceFromBottom', 'bounceFromLeft', 'bounceFromRight', 'rotateLinear' |



**Example**  
```js
x5engine.imShowBox({
	media: [
		{
			url:'myimage1.jpg',
			width: 800,
			height: 400
		},
		{
			url:'myimage2.jpg',
			width: 800,
			height: 600
		}
	]
});
```
