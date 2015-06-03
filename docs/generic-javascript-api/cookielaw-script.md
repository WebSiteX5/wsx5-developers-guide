## x5engine.cookielaw

WebSite X5 provides a banner useful to meet the <a href="http://ec.europa.eu/ipg/basics/legal/cookies/index_en.htm" target="blank" rel="nofollow">Cookie Law</a> requirements.
When the user interacts with the banner an event is triggered. See below how to use it.

### x5ActivateCookieScripts
This event is triggered whenever the user accepts the cookie policy or when a page is loaded and the cookie policy was previously accepted by the user.
**Note**: This event is triggered even if the cookie banner is not set. This means that this event is always triggered at page load in case the cookie banner is deactivated in WebSite X5.

**Kind**: event of `#imContent`

**Example**
```js
$(document).ready(function () {
	$("#imContent").on("x5ActivateCookieScripts", function () {
		console.log("The user has accepted the cookie policy");
	});
});
```

### .accepted() ⇒ <code>boolean</code>
Return `true` if the user has accepted the cookie policy.
**Note**: Use this method only if the cookie banner is active on the site.

**Kind**: Static method of `x5engine.cookielaw`

**Example**
```js
x5engine.boot.push(function () {
	if (x5engine.cookielaw.accepted()) {
		console.log("The user has accepted the cookie policy");
	}
});
```