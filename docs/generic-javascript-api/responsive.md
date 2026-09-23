<a name="module_x5engine.responsive"></a>
## x5engine.responsive
Provide a set of static methods that may help in managing the responsive features of WSX5.


* [x5engine.responsive](#module_x5engine.responsive)
  * [.getCurrentBreakPoint()](#module_x5engine.responsive.getCurrentBreakPoint) ⇒ <code>Object</code>
  * [.isDesktopMode()](#module_x5engine.responsive.isDesktopMode) ⇒ <code>Boolean</code>
  * [.isMobileDevice()](#module_x5engine.responsive.isMobileDevice) ⇒ <code>Boolean</code>
  * [.isAnyMobileDevice()](#module_x5engine.responsive.isAnyMobileDevice) ⇒ <code>Boolean</code>

<a name="module_x5engine.responsive.getCurrentBreakPoint"></a>
### .getCurrentBreakPoint() ⇒ <code>Object</code>
Get the current breakpoint.

**Kind**: static method of <code>[x5engine.responsive](#module_x5engine.responsive)</code>
**Returns**: <code>Object</code> - A JSON object containing the current breakpoint data. If no matching breakpoint is found, the method throws an error with the message `Breakpoint not found!`.
**Since**: 12.0.0  
**Example**  
```js
var data = x5engine.responsive.getCurrentBreakPoint();
// data now contains the following contents
var exampleData = {
	"name": "Desktop", // The breakpoint name
	"start": 400, // The screen width at which this breakpoint starts to be valid
	"end": 200, // The screen width at which this breakpoint ends to be valied
	"fluid": false // True if this breakpoint uses a fluid template
}
```
<a name="module_x5engine.responsive.isDesktopMode"></a>
### .isDesktopMode() ⇒ <code>Boolean</code>
Define if the current viewport is the largest one, used for desktop screens

**Kind**: static method of <code>[x5engine.responsive](#module_x5engine.responsive)</code>
**Returns**: <code>Boolean</code> - True if the current viewport is a desktop screen (largest breakpoint)  
**Since**: 12.0.0  

<a name="module_x5engine.responsive.isMobileDevice"></a>
### .isMobileDevice() ⇒ <code>Boolean</code>
Returns `true` when the viewport is within the mobile range and the device supports touch events.

**Kind**: static method of <code>[x5engine.responsive](#module_x5engine.responsive)</code>

<a name="module_x5engine.responsive.isAnyMobileDevice"></a>
### .isAnyMobileDevice() ⇒ <code>Boolean</code>
Returns `true` when `window.orientation` is available or the `(pointer: coarse)` media query matches.

**Kind**: static method of <code>[x5engine.responsive](#module_x5engine.responsive)</code>
