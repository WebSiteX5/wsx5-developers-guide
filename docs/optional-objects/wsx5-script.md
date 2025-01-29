# WSX5Script
The WSX5Script code is an ECMAScript code which is run by WebSite X5 when the HTML/CSS code is built.

The script output will be inserted where the script is.

The syntax to use is the same as JavaScript.

The script needs to be executed inside the `<?wsx5` and `?>` tags (except in the `Hooks` tag).

The following variables are defined in the code.

## parameters
**Type**: Object

Each element of this object has the properties specified in [the user input fields list](user-input-fields.md), basing on the field type.

It is defined as follows:
```javascript
var parameters = {
	"my-field-id": {

		// Hides the field in the UI.
		"hide": function () { ... },

		// Shows the field in the UI.
		"show": function() { ... },

		// True if the field is currently visible in the UI
		"visible": true,

		// Enables the field in the UI
		"enable": function() { ... },

		// Disables the field in the UI
		"disable": function () { ... },
		
		// True if the field is currently enabled
		"enabled": true,

		// Sets the field as mandatory
		"setMandatory": function() { ... },

		// Sets the field as NOT mandatory
		"setNotMandatory": function () { ... },

		// True if the field is currently mandatory
		"mandatory": false,

		// Here you can find even more fields, basing on the field type
		...
	},
	"another-field-id": {
		...
	}
};
```

## resources
**Type**: Object

A JSON object containing a JSON object for each resource id.

It is defined as follows:
```javascript
var resources = {
	"my-resource-id": {

		// The resource id
		"id": "my-resource-id",

		// The resource file name
		"name": "resource.js",

		// The destination path of this resource file
		"destination": "res/resources.js"
	},
	"another-resource-id": {
		...
	}
};
```

## storage
**Type**: Object

**Since**: 2021.5.5

Allows you to read the data from [Storage](storage.md).

It is defined as follows:
```javascript
var storage = {
	// Returns the string value corresponding to requested key
	// If the key cannot be found, it returns null
	"getString": function (key) { ... },

	// Returns the field value corresponding to requested key
	// If the key cannot be found, it returns null
	"getField": function (key) { ... }
};
```

Field value structure is defined in [Available Field Types](user-input-fields.md#available-field-types)

## document
**Type**: Object

A JSON object that allows you to output your custom code to the object's output and handle raw links.

It's defined as follows:
```javascript
var document = {

	// Write a string to the objects output
	"write": function(string) { ... },

	// Include an external file. The file will be parsed
	// and the output will be added to the document.
	// The filePath must be given starting from the app root.
	"include": function (filePath) { ... },

	// Gets the JS for the given raw link.
	// Since: 2021.3.2.0
	"rawLinkToJS": function (rawLink) { ... },

	// Decorates the given HTML with the given raw link.
	// Since: 2021.3.2.0
	"rawLinkToHTML": function (rawLink, html) { ... }
};
```

**Since**: 15.2.0

A faster way to write to the output is to use the following sintax:

```php
<?="my own string"?> // This outputs "my own string"

<?=myOwnVariable?> // This outputs the contents of myOwnVariable
```

## console
**Type**: Object

A JSON object that allows you to output some string to the dev's console.

It's defined as follows:
```javascript
var console = {

	// Write a string to the dev's console, visible when the object is in dev mode
	"log": function(string) { ... }
};
```

### Example: Output a text to the console
```javascript
console.log("This message will be output to the developer's console");
```

## currentObject
**Type**: Object

A JSON object that contains some useful information about the current object.

Is defined as follows:
```javascript
var currentObject = {
	
	// The object id
	"id": "current-object-id",

	// Tells if the object belong to a page (instead of the template). Available since v13.0.1.15
	"isPageObject": true,

	// The largest width that the object can reach in a breakpoint. Here for backward compatibility.
	"width": 400,

	// The object width at each breakpoint
	"widths": {
		"Desktop": 400,
		"Breakpoint1": 350,
		"Breakpoint2": 250,
		// Always rely on the "fluid" property of the breakpoints you get from the
		// "wsx5" object! If the breakpoint is fluid you should not use this value
		// but rather set the object's content to 100% width. This is always true
		// for the smallest breakpoint.
		"Smartphone": 200
	},

	// If true, the object will be large as the viewport. Available since v17
	"fullWidth": true

	// If true, the object will have to implement lazy loading on img tags. Available since v2022.3
	"lazyLoad": true
};
```

## l10n
**Type**: Object

Allows you to get the localizations defined in the localizations.xml file or in the website localizations or in the global localizations container of WSX5.

It's defined as follows:
```javascript
var l10n = {

	// returns the localization from localizations.xml file in the website language.
	"get": function(localizationId) { ... },

	// returns the localization from localizations.xml file in the website language.
	// If localizationId is not found, returns defaultValue.
	"get": function(localizationId, defaultValue) { ... },

	// returns the localization from localizations.xml file in the specified language,
	// returning defaultValue id localizationId is not found
	"get": function(localizationId, defaultValue, languageId) { ... },

	// returns the localization from the website localizations in the website language.
	// Available since v2024.1
	"get_website": function(localizationId) { ... },

	// returns the localization from the website localizations in the website language.
	// If localizationId is not found, returns defaultValue.
	// Available since v2024.1
	"get_website": function(localizationId, defaultValue) { ... },

	// returns the localization from the website localizations in the specified language,
	// returning defaultValue id localizationId is not found
	// Available since v2024.1
	"get_website": function(localizationId, defaultValue, languageId) { ... },

	// returns the requested localization by taking it from
	// the localization library of the UI of WebSite X5.
	// It is always in the installation language of the software.
	// Prior to v2024.1 this function was named get_global
	"get_ui": function(localizationId) { ... },

	// returns the requested localization by taking it from the
	// localization library of the UI of WebSite X5.
	// It is always in the installation language of the software.
	// In case the localization is not present it will be used the default value.	
	// Prior to v2024.1 this function was named get_global
	"get_ui": function(localizationId, DefaultValue) { ... }
};
```

### Example: get the value of a localization defined in the localizations.xml file.

```javascript
var localizedText = l10n.get("localization-id-1");
var localizedGermanText = l10n.get("localization-id-1", "DE");
```

## wsx5
**Type**: Object

Contains some information about the WSX5 state.

It is defined as follows:
```javascript
var wsx5 = {
	
	// UI language ID
	"uiLanguageId": "en",

	// Site's content language ID
	"contentLanguageId": "it",

	// WebSite X5 version. Available since 11.0.0.3
	"version": "12.0.4.21",

	// WebSite X5 edition name. Available since 11.0.0.3
	"edition": "Professional",

	// The current WSX5 mode.
	// Possible values:
	// "uipreview" : during the preview in the UI of WSX5,
	// "preview"   : during the preview in the embedded browser of WSX5,
	// "online"    : when the website is published,
	// according to the moment when the content is made
	"mode": "uipreview",

	// Get the url of a specific path (String) in the project. Available since 11.0.8.x
	"getSiteUrl": function (path) { ... },

	// The Res path folder. Available since v.17
	"pathResFolder": "../../res/",

	// Maximum width (in px) defined in w5 for full width mode. Available since v.17
	"fullWidthMaxWidth": 2460,

	// True if the website is responsive, false if only desktop. Available since v.17
	"responsiveEnabled": true,

	// The available breakpoints array.
	// Its minimum size is 1, the maximum is up to the user.
	"breakpoints":
		[
			{
				"name": "breakpoint1",

				// The maximum screen width for this breakpoint.
				// Max means that this goes from "end" to infinite
				"start": "max", 

				// The minimum screen width for this breakpoint
				"end": 400,

				// If true it means that the objects should be at
				// 100% width when this breakpoint is in use
				"fluid": false
			},
			{
				"name": "breakpoint2",

				// The maximum screenwidth for this breakpoint
				"start": 600, 

				// The minimum width. "0" means that this goes
				// down to the smallest screen available.
				"end": 0,
				
				"fluid": true
			}
	    ],

	// Informations about the private area (defined only if the private area is enabled)
	"accessManagement": {

		// The administrator email address
		"adminEmail": "info@websitex5.com",

		// The database id where the users are stored
		"dbId": "dbid-1",

		// The database table where the users are stored
		"dbTable": "users",

		// True if the captcha is enabled
		"enableCaptcha": true,

		// True if the site owner is being notified of the new subscriptions
		"notifyUser": true,

		// True if a user must validate his email address
		"validationRequired": true,

		// The array of user groups
		"groups": [
			{
				"id": "gid-1",
				"name": "Group 1",
				"gropup": "",
			},
			{
				"id": "gid-2",
				"name": "Group 2, subgroup of group 1",
				"gropup": "gid-1",
			}
		],

		// The array of user ids
		"userIds": [
			{
				"id": "uid-1",
				"name": "John Doe",
				"email": "jdoe@websitex5.com",
				"groupId": "gid-1"
			}
		]
	},

	// Informations about the shopping cart (defined only if the shopping cart is enabled).
	// The following data is available only if the ShoppingCart
	// dependency has been set. See the dependencies section
	// for more informations.
	"shoppingCart": {

		// The db used to store the orders
		"dbId": "dbid-1"

		// The db table prefix used to store the orders data
		"dbTable": "orders_",

		// The order send mode
		"sendMode": "email", // may be "email" or "db"
		
		// True if option for automatic registration of users is enabled 
		"registerCustomers" : true,
		// True if user choose to alternate row's background color
		"ZebraTable":true,
		// Color type
        "CellTextColor":{
            "a":255,
            "r":37,
            "g":58,
            "b":88
		 },
		// Color type
        "CellBackgroundColor": {  },
		// Color type
		"HeadTextColor": {  },
		// Color type
		"HeadBackgroundColor": {  },
		// Color type
		"TableBorderColor": {  },
		// Radius type
        "TableBorderRadius": {
            "top":2,
            "right":2,
            "bottom":2,
            "left":2
        },
		// Cart coupon codes
		"coupon": [
			{
				"id": "COUPON_01",
				"type": "absolute", // Fixed (absolute) or percentage (relative)
				"discount": 10,
				"startDate": ""
				"endDate": ""
			},
			{
				"id": "COUPON_02",
				"type": "relative", // Fixed (absolute) or percentage (relative)
				"discount": 10,
				"startDate": "2018-11-06T17:28:28"
				"endDate": "2018-11-24T17:28:28"
				"applyOnShippingAndPayment": true
			}
		],
		// The following data is available only if ShoppingCart and ShoppingCartProducts
		// dependencies have been set. See the dependencies section
		// for more informations.
		"products": [
			{
				"id": "",
				"name": "",
				"description": "",
				"price": 0,
				"lowestPrice": 0, // available since v2024.4; -1 if user doesn't want to show previous price
				"vat": 0,
				"weight": 0,
				"coupon": "",
				"category": "",
				// Fixed discount
				"fixedDiscount": {
					"startDate": "",
					"startDateActive": false,
					"endDate": "",
					"endDateActive": false,
					"absolute": 0,
					"coupon": "",
					"couponEnabled": false,
					"relative": 0,
					"enabled": false,
					// none, relative or absolute
					"type": "none"
				},
				// Quantity discount
				"quantityDiscount": {
					"enabled": false,
					"pairs": [
						{
							"minimum": 0,
							"value": 0,
						}
					]
				},
				// Images
				"images": [
					{
						"width": " + image.Width + ",
						"height": " + image.Height + ",
						"path": '" + Helper.JSONEscape(fg.Destination) + "'
					}
				],
            }
		],
		// The following data is available only if ShoppingCart and ShoppingCartPayments
		// dependencies have been set. See the dependencies section
		// for more informations.
		"payments": [
			{
				"id": "",
				"description": "",
				"emailMessage": "",
				"enableVat": false,
				"name": "",
				"image": "",
				"percentualPrice": 0,
				"price": 0,
				"vat": 0,
				// fixed or percentual
				"priceType": "fixed"
				},
			}
		],
		// The following data is available only if ShoppingCart and ShoppingCartShippings
		// dependencies have been set. See the dependencies section
		// for more informations.
		"shippings": [
			{
				"id": "",
				// Quantity Discounts
				"quantityDiscounts": [
					{
						"minimum": 0,
						"value": 0,
					}
				],
				// Weight Discounts
				"weightDiscounts": [
					{
						"minimum": 0,
						"value": 0,
					}
				],
				"description": "",
				"emailMessage": "",
				"enableVat": false,
				"image": "",
				"name": "",
				"price": 0,
				"vat": 0,
				// fixed, totalAmountRelated or totalWeightRelated
				"priceType": "fixed"
			}
		]
	},

	// Informations about the blog
	// The following data is available only if the Blog
	// dependency has been set. See the dependencies section
	// for more informations.
	"blog": {
		"allowComments": false,
		"description": "",
		"id": "",
		"title": "",
		// The list of posts in the blog
		"items": [
			{
				"author": "",
				"description": "",
				"category": "",
				"cover": "",
				"date": new date(),
				"content": "",
				"title": "",
				// The images loaded in the post text
				"images": [
					{
						"path": "",
						"alignment": "",
						"alt": "",
						"height": 0,
						"width": 0,
						"title": ""
					}
				],
				// HTML code of the media attached to this post
				"media": ""
			}
        ]
	},

	// Informations about the RSS Feed
	// The following data is available only if the RSSFeed
	// dependency has been set. See the dependencies section
	// for more informations.
	"rssFeed": {
		"description": "",
		"title": "",
		"image": "", // Available since v.17
		// The list of posts in the feed
		"items": [
			{
				"date": new date(),
				"content": "",
				"title": "",
				// The images loaded in the post text
				"images": [
					{
						"path": "",
						"alignment": "",
						"alt": "",
						"height": 0,
						"width": 0,
						"title": ""
					}
				]
			}
        ]
	},

	// Informations about the data managements
	// The following data is available only if the DataManagement
	// dependency has been set. See the dependencies section
	// for more informations.
	"dataManagement": {
		
		// True if the value specified in commonEmailAddress
		// should be used for the email messages
		"useCommonEmailAddress": true,

		// The email address the user defined as sender for 
		// every email message sent from the current website
		"commonEmailAddress": "info@websitex5.com",

		// An array of database data
		"databases": [
			{
				"id": "dbid-1",
				"description": "The db 1 description",
				"name": "Database 1",
				"host": "host-1.example.com",
				"user": "user-1",
				"password": "p@SsW0rd-1",
				"prefix": "prefix_1_"
			},
			{
				"id": "dbid-2",
				"description": "The db 2 description",
				"name": "Database 2",
				"host": "host-2.example.com",
				"user": "user-2",
				"password": "p@SsW0rd-2",
				"prefix": "prefix_2_"
			}
		],

		// The method that the user defined to submit the form
		"formSubmitType": "get", // or "post"

		// The public folder path based on the site's root
		"publicFolder": "",
	},

	// Since v2019.1.0.0
	// Informations about the menu
	// The following data is available only if the SiteElements
	// dependency has been set. See the dependencies section
	// for more informations.
	"menu": {
		"nodes": [ // The menu tree structure
			{
				"type": "page",  // See the other types below
				"id": page-id,
				"parentId": parent-id,
				"label": "the page name"
				"destination": "the page absolute url",				
				"isWorking": false, // True if this was set as "working page" by the user
				"isHidden": false, // True if this page was set as hidden in the menu
				"isLocked": false, // True if this page is available only for logged users
				"isSpecial": false, // True if this page is special (Search, Blog, etc...)
				"isNotInMenuTree": false, // True if this page doesn't exist in menu tree
				"isHomePage": false, // True if this page is the Home
				"pageType": "grid",
				"grantedGroups": [], // Array of users groups ids that may access to this page (only if isLocked == true)
				"grantedUsers": [], // Array of users ids that may access to this page (only if isLocked == true)
				"position": 0, // Position inside the parent node (start with 0)
				"onclick": "onclick='function to execute to go to this page'",
				"paths": [ 'page relative url' ], // paths used for current page management, see x5engine.utils.isCurrentPage(paths, anchor)",
				"icon": "the icon absolute url, empty string if no icon was setted by user"
			},
			{
				"type": "separator",
				"id": separator-id,
				"parentId": parent-id,
				"label": "the separator name",
				"isHidden": false,
				"isNotInMenuTree": false,
				"position": 1
			},
			{
				"type": "level",
				"id": level-id,
				"parentId": parent-id,
				"label": "the level name",
				"isHidden": false,
				"isSpecial": false,
				"isNotInMenuTree": false,
				"hideSubMenu": false, // True if user check the "hide submenu" option
				"position": 2,
				"onclick": "onclick='function to execute to go to this level link'",
				"paths": [], // paths used for current page management, see x5engine.utils.isCurrentPage(paths, anchor)",
				"icon": "icon url",
				"anchor": "like data-anchor of the ObjectMenu",
				"hash": "like data-hash of the ObjectMenu",
				"nodes": [ // An array of elements just like the current one
					{
						"type": "page",
						"id": subpage-id,
						"parentId": level-id, // parentId is the level one
						"position" : 0, // position start again with 0
						..
						..
					},
					{
						"type": "level",
						"id": sublevel-id,
						"position": 1,
						"nodes" : [ .. ], // Ando so on
						..
						..
					}
				]
			}
		],
		"pathMap": { // Object internally used to obtain the positions path of an element from its id
			"page-id": [0],
			"separator-id": [1],
			"level-id": [2],
			"subpage-id": [2, 0],
			"sublevel-id": [2, 1],
			..
			..
		},
		"getNode": function(id){ .. }, // return the node with the id used as argument
		"getNodeFromPath": function(path) { .. }, // return the node positioned at path used as argument
		"getPath": function(id) { .. } // return the position path of the node with id used as argument
	}

	// Informations about the default styles
	// The following data is available only if the ModelStyle
	// dependency has been set. See the dependencies section
	// for more informations.
	"defaultStyles":{
         "activeLink":{
            "textStyle":{  },
				// Color type
				"backgroundColor":{ },
				// Color type
               "textColor":{ },
               "textAlignment":"left",
               "familyName":"Tahoma",
               "size":9,
               "style":"regular" // can be "regular", "bold", "italic", "underline"
            },
            "decoration":"underline" // can be "none" or "underline"
        },
         "body":{
            "textStyle":{
				// Color type
               "backgroundColor":{ },
			   // Color type
               "textColor":{ },
               "textAlignment":"left",
               "familyName":"Tahoma",
               "size":10,
               "style":"regular"
            }
        },
         "button":{
            "backColor":{ },
            "border":{
				// Color type
               "bottomColor":{ },
			   // Color type
               "leftColor":{ },
			   // Color type
               "rightColor":{ },
			   // Color type
               "topColor":{ },
               "bottomLeftRadius":0,
               "bottomRightRadius":0,
               "topLeftRadius":0,
               "topRightRadius":0,
               "bottomWidth":1,
               "leftWidth":1,
               "rightWidth":1,
               "topWidth":1
            },
			// Color type
            "foreColor":{ },
			// Padding type
            "padding":{
               "top":8,
               "right":4,
               "bottom":8,
               "left":4
            }
        },
		 // Standard date format in .NET notation. Available since v2024.1
         "dateFormat": "dd/MM/yyyy",
		 // Extended date format in .NET notation. Available since v2024.1
         "dateFormatExt": "ddd dd MMM yyyy",
		 // Return "date" formatted as string using standard/extended format (depending on "extented" value) or using "format" (if provided)
		 // Available since v2024.1
		 "formatDate": function(date, extended, format) { .. },
         "field":{
			 // Color type
            "backColor":{ },
            "border":{
				// Color type
               "bottomColor":{ },
			   // Color type
               "leftColor":{ },
			   // Color type
               "rightColor":{ },
			   // Color type
               "topColor":{ },
               "bottomLeftRadius":0,
               "bottomRightRadius":0,
               "topLeftRadius":0,
               "topRightRadius":0,
               "bottomWidth":1,
               "leftWidth":1,
               "rightWidth":1,
               "topWidth":1
            },
			// Color type
            "foreColor":{ },
            "innerShadow":false,
			// Padding type
            "padding":{ }
        },
         "hoverLink":{
            "textStyle":{
				// Color type
               "backgroundColor":{ },
			   // Color type
               "textColor":{ },
               "textAlignment":"left",
               "familyName":"Tahoma",
               "size":9,
               "style":"regular"
            },
            "decoration":"none"
        },
         "path":{
            "horizontalMargin":6,
			// Color type
            "lineBottomColor":{ },
			// Color type
            "lineLeftColor":{ },
			// Color type
            "lineRightColor":{ },
			// Color type
            "lineTopColor":{ },
            "textStyle":{
				// Color type
               "backgroundColor":{ },
			   // Color type
               "textColor":{ },
               "textAlignment":"left",
               "familyName":"Tahoma",
               "size":7,
               "style":"regular"
            }
        },
         "title":{
            "horizontalMargin":6,
			// Color type
            "lineBottomColor":{ },
			// Color type
            "lineLeftColor":{ },
			// Color type
            "lineRightColor":{ },
			// Color type
            "lineTopColor":{ },
            "textStyle":{
				// Color type
               "backgroundColor":{ },
			   // Color type
               "textColor":{ },
               "textAlignment":"left",
               "familyName":"Tahoma",
               "size":12,
               "style":"bold"
            }
        },
         "visitedLink":{
            "textStyle":{
				// Color type
               "backgroundColor":{ },
			   // Color type
               "textColor":{ },
               "textAlignment":"left",
               "familyName":"Tahoma",
               "size":9,
               "style":"regular"
            },
            "decoration":"underline"
        }
    }
};
```

## wsx5utils
**Type**: Object

Contains some helper functions.

It is defined as follows:
```javascript
var wsx5utils = {
	// Replace HTML entities (like &amp;, &apos;, ...) with the corresponding characters
	"decodeHTMLEntities": function (htmlStr) { ... },
	
	// Escape a string for regular expression use
	"escapeRegExp": function (string) { ... },
	
	// Replace all occurrences of the string "find" with the string "replace" inside the string "str"
	"replaceAll": function (str, find, replace) { ... },
	
	// Escape a string to be used in JS code
	"JSEscape": function (text) { ... }
};
```
