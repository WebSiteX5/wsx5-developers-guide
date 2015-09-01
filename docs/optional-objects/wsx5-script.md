# WSX5Script
The WSX5Script code is an ECMAScript code which is run by WebSite X5 when the HTML/CSS code is built.
The script output will be inserted where the script is.
The syntax to use is the same as JavaScript.
The script needs to be executed inside the `<?wsx5` and `?>` tags (except in the `Hooks` tag).

The following variables are defined in the code.

## parameters
Type: Object
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
		
		// True if the field is currenlty enabled
		"enabled": true,

		// Here you can find even more fields, basing on the field type
		...
	},
	"another-field-id": {
		...
	}
};
```

## resources
Type: Object
A JSON object containing a JSON object for each resource id. It is defined as follows:
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

## document
Type: Object
A JSON object that allows you to output your custom code to the object's output.
It's defined as follows:

```javascript
var document = {

	// Write a string to the objects output
	"write": function(string) { ... }
};
```

## console
Type: Object
A JSON object that allows you to output some string to the dev's console.
It's defined as follows:

```javascript
var console = {

	// Write a string to the dev's console, visible when the object is in dev mode
	"log": function(string) { ... }
};
```

## currentObject
Type: Object
A JSON object that contains some useful information about the current object.
Is defined as follows:

```javascript
var currentObject = {
	
	// The object id
	"id": "current-object-id",

	// The object width
	"width": 400
};
```

## l10n
Type: Object
Allows you to get the localizations defined in the localizations.xml file or in the global localizations container of WSX5.
It's defined as follows:

```javascript
var l10n = {

	// returns the localization in the website language.
	"get": function(localizationId) { ... },

	// returns the localization in the website language. If localizationId is not found, returns defaultValue.
	"get": function(localizationId, defaultValue) { ... },

	// returns the localization in the specified language, returning defaultValue id localizationId is not found
	"get": function(localizationId, defaultValue, languageId) { ... },

	// returns the requested localization by taking it from the localization library of the UI of WebSite X5.
	// It is always in the installation language of the software.
	"get_global": function(localizationId) { ... },

	// returns the requested localization by taking it from the localization library of the UI of WebSite X5.
	// It is always in the installation language of the software. In case the localization is not present it will be used the default value.	
	"get_global": function(localizationId, DefaultValue) { ... }
};
```

An example: get the value of the localization defined as "localization-id-1" in the localizations.xml file.

```javascript
var localizedText = l10n.get("localization-id-1");
var localizedGermanText = l10n.get("localization-id-1", "DE");
```

## wsx5
Type: Object
Contains some information about the WSX5 state.
It is defined as follows:

```javascript
var wsx5 = {
	
	// UI language ID
	"uiLanguageId": "en",

	// Site's content language ID
	"contentLanguageId": "it",

	// The current WSX5 mode
	"mode": "uipreview", // May be 'uipreview', 'preview', 'online', according to the moment when the content is made

	// Get the url of a specific path (String) in the project. Available since 11.0.8.x
	"getSiteUrl": function (path) { ... },

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
				"username": "jdoe",
				"groupId": "gid-1"
			}
		]
	},

	// Informations about the shopping cart (defined only if the shopping cart is enabled)
	"shoppingCart": {

		// The db used to store the orders
		"dbId": "dbid-1"

		// The db table prefix used to store the orders data
		"dbTable": "orders_",

		// The order send mode
		"sendMode": "email" // may be "email" or "db"
	},

	// Informations about the data managements
	"dataManagement": {
		
		// True if the value specified in commonEmailAddress should be used for the email messages
		"useCommonEmailAddress": true,

		// The email address the user defined as sender for every email message sent from the current website
		"commonEmailAddress": "info@websitex5.com",

		// An array of database data
		"databases": [
			{
				"id": "dbid-1",
				"description": "The db 1 description",
				"name": "Database 1"
			},
			{
				"id": "dbid-2",
				"description": "The db 2 description",
				"name": "Database 2"
			}
		],

		// The method that the user defined to submit the form
		"formSubmitType": "get", // or "post"

		// The public folder path based on the site's root
		"publicFolder": "",
	}
};
```
