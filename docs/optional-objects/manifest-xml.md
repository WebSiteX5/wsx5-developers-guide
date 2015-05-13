# Manifest File

Describes the Object structure and features and contains the links to the resource files, the Object’s code, and the user interface descriptors.

Here's how a manifest.xml looks like:
```xml
<App uuid="4x34js230s2304u3234s30492">
	<!-- Here there is the object's metadata -->
	<Name>Hello World</Name>
	<Author>Me</Author>
	<Version>1</Version>
	<Category>Widgets</Category>
	<Description l10n-id="description">Add a "Hello World!" to your page.</Description>
	<!-- Here we define the user input fields -->
	<Parameters>
		<Tab>
			<Label>I'm a tab</Label>
			<Field type="text" id="name">
				<Label>Type your name here</Label>
				<DefaultValue>World</DefaultValue>
			</Field>
		</Tab>
	</Parameters>
	<!-- Here we define the output -->
	<Output><[CDATA["Hello World!" by <?wsx5 document.write(parameters['name'].value); ?>]]></Output>
</App>
```

Below here you can find a list of the supported tags.

## App Tag
**Mandatory**: yes
It is the opening tag. It has the attribute uuid which identifies the app uniquely. 

```xml
<App uuid="application-id">
```

## Name Tag
**Mandatory**: yes
It contains the name of the application.

```xml
<Name>Name of the app</Name>
```

## Version Tag
**Mandatory**: yes
It contains a integer to identify the version of the application.

```xml
<Version>1</Version>
```

## MinimumWebSiteX5Version Tag
**Mandatory**: no
It contains the minimum required version of WebSiteX5 to run the optional object.

```xml
<MinimumWebSiteX5Version>11.0.0.1</MinimumWebSiteX5Version>
```

## Category Tag
**Mandatory**: yes
It contains the ID of the category where the app will be available.

```xml
<Category>Category of the Application</Category>
```

## Description Tag
**Mandatory**: yes
It contains the description of the application. It can be localized with the `l10n-id` and `global-l10n-id` attributes. 

```xml
<Description l10n-id="description">Description of the Application</Description>
```

## PageExtension Tag
**Mandatory**: no
If defined it contains the extension of the page required to allow the code of the Object to work correctly. The extension has to be added without characters like "*.".
For example, to require a php extension it is only necessary to write:

```xml
<PageExtension>php</PageExtension>
```

## CustomHeight Tag
**Mandatory**: no
If provided and has an integer numerical value higher than zero, it indicates the height of the object. If provided, the automatic height calculation will be deactivated.

```xml
<CustomHeight>100</CustomHeight>
```

## Parameters Tag
**Mandatory**: no
It contains a list of `Tab` tags which represents every Tab shown in the Object’s UI.

Each `Tab` tag may have an id attribute and may contain the following subtags.

| Subtag Name | Default value | Description |
|-------------|---------------|-------------|
| Label | (empty) | Set the tab’s label shown in the UI. It may have the `l10n-id` or `global-l10n-id` attributes for localization purposes. |
| ShowPreview | `false` | If set to `true` shows the preview in the selected tab. |
| Fields | (empty) | See the [User input fields](user-input-fields.md) section.|

```xml
<Parameters>
	<Tab id="my-tab">
		<Label l10n-id="my-tab-l10n-id">My Tab</Label>
		<ShowPreview>true</ShowPreview>
		<Fields>
			<!-- Put here the Field tags -->
		</Fields>
	</Tab>
	<Tab id="another-tab">
		<Label l10n-id="anotehr-tab-l10n-id">Another Tab</Label>
		<Fields>
			<!-- These fields will be shown when this tab is visible -->
		</Fields>
	</Tab>
</Parameters>
```

## Resources Tag
**Mandatory**: no
If defined, it contains a list of `Resource` tags. Each of them defines the operations to perform on the files available in the **Resources** folder of the application.

Each `Resource` tag can have the following properties:

|Property name|Mandatory|Default value|Description|
|-------------|---------|-------------|-----------|
|id | no | (empty) | A unique ID assigned to the resource useful to access to the resource data via the [WSX5 Script](wsx5-script.md) code.|
|src |yes| |The source path of the file relative to the "Resources" folder of the application. You cannot provide a path outside that folder, that is, provide a path that contains the "../" string.|
|action|no|copy| May contain "copy" or "process". If "copy", the file will be copied as is by WebSite X5. If "process", the content of the file will be elaborated according the same rules used for the content of the [Output tag](manifest-xml.md#output-tag)|
|autolink|no|`false`| If the linked file is a js or css file and this field is set to "true", the file will be automatically linked in the header of the website page.|
|shared|no|`false`|If set to "true" the resource will be copied only once in a shared folder for all objects of this type. This will allow to avoid duplicated copies of a static file.|
|offlineonly|no|`false`|If `true`, the resource will be copied or processed only while in offline mode (UI preview and site preview).|

In the following example, two files are linked in the manifest.
The first (jquery-ui.min.js) is copied as is, automatically linked in the site’s header and shared between all the objects of the same type in the page.
The second file is a custom JavaScript file that needs to be processed before being linked in the site’s header. Since it’s processed, its content may depends on the user input, therefore it’s not shared between the objects of the same type in the page.

```xml
<Resources>
    <Resource src="jquery-ui.min.js" action="copy" autolink="true" shared="true" />
    <Resource src="mysourcefile.js" action="process" autolink="true" />
</Resources>
```

## ShowPreview Tag
**Mandatory**: no
If set as `true`, the UI of WebSite X5 will show a preview of the object directly in the window where the input fields are available.

## Output Tag
**Mandatory**: yes
This tag contains the code which has to be used to create the HTML code to insert inside the site page.
This tag may contain any kind of code. It will be then copied inside the code of the page.
Inside this tag you can write [WSX5 Script](wsx5-script.md) code. It must be executed within the `<?wsx5` and `?>` tag. This code follows the guidelines described in the [WSX5 Script](wsx5-script.md) section.

## PreviewOutput Tag
**Mandatory**: no
If available, it contains the output HTML code to show in the preview. Works like the Output tag.

## UIPreviewOutput Tag
**Mandatory**: no
If available, it contains the output HTML code to show in the small preview visible in the UI. Works like the Output tag.
