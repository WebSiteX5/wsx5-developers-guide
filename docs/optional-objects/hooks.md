# Hacking the default behavior
You can change the default behavior of an optional object by specifying some hook function that will be called during the object's output building phase.

The script functions should be defined in the `Hooks` tag, placed inside the `App` tag.
This tag contains the WSX5Script code which has to be run in specific moments in the creation of the object. The script can define following functions. 

## GetHeight()
If the `CustomHeight` tag has not been set in the XML code of manifest, this function will be called every time it will be necessary to calculate the height of the object.
It must return an integer value greater than zero representing the height of the object. 

If the CustomHeight tag has not been set in the manifest and this function is not defined, WebSite X5 will use its own height algorithm, that is, WebSite X5 will be less precise.

## IsEmpty()
If defined, this function must return `true` if the object has to be considered empty (so not shown in the page), `false` otherwise.

## ShowPreview()
**Since:** 11.0.4
If defined, this function must return `true` if the object is able to show the preview in the software's UI, `false` otherwise.

## GetHeaderContents(type, currentContent)
If defined, this function allows the author to specify a custom code to include in the head tag of the website. It must return a string, which will be included in the site's header in the position relative to the "type" parameter.

|Parameter     | Type   | Description                                                           |
|--------------|--------|-----------------------------------------------------------------------|
|type          |`String`|Indicates the required type of content. Can be "js", "css", "other".   |
|currentContent|`String`|Contains the current headers for the type of code specified via the "type" parameter. It is useful to verify to not add a duplicated code.|

This function may be called more than once during the creation of the page code (more precisely, one time for every possible value of the "type" parameter).
To avoid the duplication of the code, the programmer must always verify the value of `type` and
`currentContent` and act consequently, as in the example below.

```javascript
function GetHeaderContents(type, currentContent) {
	// Include my own js library in the site's header, making sure it was not yet included
	if (type == 'js' && currentContent.indexOf('mylibrary.js') == -1) {
		return '<script src="http://mysite.com/mylibrary.js"></script>';
	}
	// Include my own css style
	if (type == 'css' && currentContent.indexOf('.myclass { border: 1px solid black; }')) {
		return '<style type="text/css">.myclass { border: 1px solid black; }</style>';
	}
	return "";
}
```

## OnBeforeFileElaboration(fieldID, file)
This function is called every time the object elaborates a generic file selected by the user except images (for images see the [OnBeforeImageElaboration](#onbeforeimageelaborationfieldid-image) hook).

|Parameter | Type   | Description                                                                                     |
|----------|--------|-------------------------------------------------------------------------------------------------|
| fieldID  |`String`| Contains the ID of the form field which has been used by the final user for the file selection. |
| file     |`Object`| Contains the JSON object which allows to access to the file data and to perform commands on it. |

The **file** parameter is defined as follows (the code is filled with example values):
```javascript
{
	// Name of the file that is going to be processed
	"name": "filename.txt",

	// Just a little helper: the extension of the file.
	"extension": ".txt",

	// true if the creation of this file is already prevented (so it won't be created)
	"isCreationPrevented": false,

	// Call this function if you want to prevent the creation of this file
	"preventCreation": function () { ... },

	// In case this is a plain text file, this string contains the file content.
	//  You can set it to actually change the file content (see the example below).
	"content": "current file content"       
}
```

This is a simple example of this hook. Here we change the content of the file "example.txt" selected by the user.

```javascript
function OnBeforeFileElaboration(fieldID, file) {
	// Since this hook is called for every file selected by the user, let's check the file name 
	// before proceeding. We want to modify 'example.txt' only.
	if (file.name == 'example.txt') {
	 	// Add a new line to the file. This will change the exported file content.
		file.content = file.content + "my new content";
	}
}
```

## OnBeforeImageElaboration(fieldID, image)
This function is called every time the object elaborates an image file selected by the user.

|Parameter | Type   | Description                                                                           |
|----------|--------|---------------------------------------------------------------------------------------|
|fieldID   |`String`| Contains the ID of the form field which has been used by the user to select the file. |
|image     |`Object`|Contains the JSON object which allows to access the the image data and to perform some operations of it.|

The **image** parameter is a JSON object defined as follows (the code is filled with example values):

```javascript
{
	// NOTE:
	// It has the same attributes defined for the "file" parameter of "OnBeforeFileElaboration"
	// plus the following ones..

	// The original image width
	"sourceWidth": 100,

	// The original image height
	"sourceHeight": 150,

	// Set this property to change the output image width
	"outputWidth": 100,

	// Set this property to change the output image height
	"outputHeight": 150,

	// Call this function to create a clone of the image with different dimensions.
	// This is useful if you want to create thumbnails!
	"clone": function(filename, width, height) { ... } 
}
```

## OnBeforeResourceElaboration(resourceID, resource)
**Since**: 11.0.4
This function is called everytime the object elaborates a resource file linked in the manifest.

|Parameter | Type   | Description                                                                                                    |
|----------|--------|----------------------------------------------------------------------------------------------------------------|
|resourceID|`String`| Contains the resource ID                                                                                       |
|resource  |`Object`| Contains a JSON object which allows to access to the data of the resource and to perform some operations on it.|

The **resource** parameter is defined as follows (the code is filled with example values):
```javascript
{
	// The original file name
	"name": "jquery.js",

	// The file extension
	"extension": ".js",

	// The destination path of this file based on the site's root folder
	"destination": "res/jquery.js",

	// True if this file won't be created
	"isCreationPrevented": false,

	// Call this function to prevent the creation of this resource
	"preventCreation": function () { ... }
}
```