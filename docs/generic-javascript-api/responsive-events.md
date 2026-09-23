# Responsive Events

The X5 Engine API provides you a set of responsive-related events.
**All the events listed below are triggered on the ```#imContent``` DOM element**.

### beforeBreakpointChanged
This event is emitted immediately before `breakpointChanged` when a window resize changes the responsive breakpoint. It is a notification event, not a cancellable event.

**Kind**: Event
**Since**: 12.0.0
**Example**:
```js
$("#imContent").on("beforeBreakpointChanged", function (e, breakpoint) {
	// The breakpoint is passed as argument to the event handler and has 
	// the same structure returned by x5engine.responsive.getCurrentBreakPoint();
	alert('The current viewport is going to change to ' + breakpoint.name);
});
```


### breakpointChanged
This event is triggered every time a window resize triggers a breakpoint change in the responsive template.

**Kind**: Event
**Since**: 12.0.0
**Example**:
```js
$("#imContent").on("breakpointChanged", function (e, breakpoint) {
	// The breakpoint is passed as argument to the event handler and has 
	// the same structure returned by x5engine.responsive.getCurrentBreakPoint();
	alert('The current viewport is changed to ' + breakpoint.name);
});
```


### breakpointChangedOrFluid
This event is triggered every time a window resize triggers a breakpoint change or everytime the window is resized in a fluid breakpoint (usually the smallest one).

**Kind**: Event
**Since**: 12.0.0
**Example**:
```js
$("#imContent").on("breakpointChangedOrFluid", function (e, breakpoint) {
	// The breakpoint is passed as argument to the event handler and has 
	// the same structure returned by x5engine.responsive.getCurrentBreakPoint();
	if (!breakpoint.fluid) {
		alert('The current viewport is changed to ' + breakpoint.name);
	} else {
		alert('The current window width is now: ' + $(window).innerWidth() + 'px');
	}
});
```
