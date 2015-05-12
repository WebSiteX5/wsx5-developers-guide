# Hacking the default behavior
You can change the default behavior of an optional object by specifying some hook function that will be called during the object's output building phase.
The script functions should be defined in the `Hooks` tag, placed inside the `App` tag.
This tag contains the WSX5Script code which has to be run in specific moments in the creation of the object. The script can define following functions. 

## `GetHeight()`
If the `CustomHeight` tag has not been set in the XML code of manifest, this function will be called every time it will be necessary to calculate the height of the object.

It must return an integer value greater than zero. 

If the CustomHeight tag has not been set in the manifest and this hook is not present, WebSite X5 will use its own height algorithm, that is, WebSite X5 will be less precise.

## `IsEmpty()`
If present, this hook has to return a boolean value.

It must return true if the object has to be considered empty, false otherwise.

## `ShowPreview()`
Availabe from Version 11.0.4. If present, this hook has to return a boolean value.

It must return true if the object is able to show the preview in the UI of the software, false otherwise.

## `GetHeaderContents(string type, string currentContent)`
This function allows the application author to specify a custom code to include in the head tag of the website.

This function has to return a string, which will be included in the best position according to the "type" parameter.

`type` indicates the required type of content and can be "js", "css", "other".

`currentContent` is a read-only string that contains the current headers for the type of code specified via the "type" parameter. It is useful to verify to not add a duplicated code.

This function can be called more times during the creation of the page code (more precisely, one time for every possible value of the "type" parameter).
To avoid the duplication of the code, the programmer has to always verify the value of the "type" parameter and act consequently.

## `OnBeforeFileElaboration(string fieldID, object file)`
This function is called every time the object elaborates a generic file selected by the user except images (for images see the next hook).

`fieldID`: contains the ID of the form field which has been used by the final user for the file selection.
`file`: contains the json object which allows to access to the file data and to perform commands on it. Has the following elements:

* name,
* extension,
* isCreationPrevented,
* preventCreation()

`content`: allows to get and set the content of the file. In this way it will be possible to modify the content of the files selected by the user

## OnBeforeImageElaboration(fieldID, image)
This function is called every time the object elaborates an image file selected by the user.
fieldID: Contains the ID of the form field which has been used by the user to select the file.
image: Contains the json object which allows to access the the image data and to perform some operations of it. In addition to the attributes present in the file parameter of the OnBeforeFileElaboration function, the parameter image is a json file which contains following items:

* sourceWidth,
* sourceHeight,
* outputWidth,
* outputHeight,
* clone(filename, width, height): creates a clone of the image with different dimensions.

## OnBeforeResourceElaboration(resourceID, resource)
Available from Version 11.0.4.
This function is called everytime the object elaborates a resource file linked in the manifest.

* resourceID: contains the ID of the resource
* resource: contains the json object which allow to access to the data of the resource and to perform some operations on it. Has the following elements:
* name: the original name of the file
* extension
* destination: the path where the file will be saved
* isCreationPrevented
* preventCreation()
