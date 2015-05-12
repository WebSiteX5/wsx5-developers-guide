# Manifest File

Describes the Object structure and features and contains the links to the resource files, the Object’s code, and the user interface descriptors.
Here you can find a list of the tags it may contain.

## App Tag
Mandatory. It is the opening tag. It has the attribute uuid which identifies the app uniquely. 

```xml
<App uuid=" UNIQUEID ">
```

## Name Tag
Mandatory. It contains the name of the application.

```xml
<Name> Name of the app </Name>
```

## Version Tag
Mandatory. It contains a integer to identify the version of the application.

```xml
<Version>1</Version>
```

## MinimumWebSiteX5Version Tag
Optional. It contains the minimum required version of WebSiteX5 to run the optional object.

```xml
<MinimumWebSiteX5Version>11.0.0.1</MinimumWebSiteX5Version>
```

## Category Tag
Mandatory. It contains the ID of the category where the app will be available.

```xml
<Category>Category of the Application</Category>
```

## Description Tag
Mandatory. It contains the description of the application. It can be localized with the l10n-id and global-l10n-id properties. 

```xml
<Description l10n-id="description">Description of the Application</Description>
```

## PageExtension Tag
Optional. If present it contains the extension of the page required to allow the code of the Object to work correctly. The extension has to be added without characters like "*.".
For example, to require a php extension it is only necessary to write:

```xml
<PageExtension>php</PageExtension>
```

## CustomHeight Tag
Optional. If provided and has an integer numerical value higher than zero, it indicates the height of the object. If provided, the automatic height calculation will be deactivated.

```xml
<CustomHeight>100</CustomHeight>
```

## Parameters Tag
Optional. It contains a list of "Tab" tags which represents every Tab shown in the Object’s UI.

Each Tab tag may have an id attribute and may contain the following subtags:

* **Label**: Set the tab’s label shown in the UI. It may have the l10n-id attribute for localization purposes.
* **ShowPreview**: if set to "true" shows the preview in the selected tab.
* **Fields**: See the following paragraph

## Resources Tag
Optional. If present, it contains a list of tag Resource. Each of them defines the operations to perform on the files available in the "Resources" folder of the application.

The tag can have following properties:

* **id**: optional, an unique ID assigned to the resource
* **src**: mandatory, the source path of the file relative to the "Resources" folder of the application. You cannot provide a path outside that folder, that is, provide a path that contains the "../" string.
* **action**: optional, may contain "copy" or "process". The default property is "copy". If "copy",the file will be copied as isby WebSite X5. If "process", the content of the file will be elaborated according the same rules used for the content in the Output tag (see below)
* **autolink**: optional. If the linked file is a js or css file and this field is set to "true", the file will be automatically linked in the header of the website page. The default value is "false".
* **shared**: optional. If set to "true" the resource will be copied only once in a shared folder for all objects of this type. This will allow to avoid duplicated copies of a static file. The default value is "false".
* **offlineonly**: the resource will be copied or processed only in the offline mode (UI preview and site preview).

### Resources XML code example
In the following example are linked two files.

The first (jquery-ui.min.js) is copied as is, automatically linked in the site’s header and shared between all the objects of the same type in the page.

The second file is a custom JavaScript file that needs to be processed before being linked in the site’s header. Since it’s processed, its content may depends on the user input, therefore it’s not shared between the objects of the same type in the page.

```xml
<Resources>
    <Resource src="jquery-ui.min.js" action="copy" autolink="true" shared="true" />
    <Resource src="mysourcefile.js" action="process" autolink="true" />
</Resources>
```

## ShowPreview Tag
Optional. If set as "true", the UI of WebSite X5 will show a preview of the object directly in the window where the input fields are available.

## Output Tag
Mandatory. This tag contains the code which has to be used to create the HTML code to insert inside the page of the website.
Inside this tag it can be added any type of code. It will be then copied inside the code of the page.
The code WSX5Script must be executed within the <?wsx5 and ?> tag. This code follows the guide lines defined in the WSX5Script paragraph.

## PreviewOutput Tag
Optional. If available, it contains the output HTML code to show in the preview. Works like the Output tag.

## UIPreviewOutput Tag
Optional. If available, it contains the output HTML code to show in the small preview visible in the UI. Works like the Output tag.
