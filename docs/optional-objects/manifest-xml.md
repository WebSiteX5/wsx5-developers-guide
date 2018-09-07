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
	<Groups>Data Visualization, Animation</Groups>
    <InitialSize>350,250</InitialSize>
    <RecommendedMinSize>100,100</RecommendedMinSize>
	<Description l10n-id="description">Add a "Hello World!" to your page.</Description>
	<!-- Here we define some cosmetics -->
	<Overflow>false</Overflow>
	<ShowPreview>true</ShowPreview>
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
	<PreviewOutput src="output/preview.html"></PreviewOutput>
</App>
```

## Loading of external content in the manifest
**Since**: 15.2.0

A tag may have an `src` property. If set, it shall contain a path to an external file that provides the content to be used for the tag.
The path indicated in the `src` property is related to the object root folder.
If the `src` property is not set, the inner text of the tag is used as content.

If the tag has an "encrypted" property set to `true`, the file indicated by the `src` property is encrypted. The property value is `false` by default.

# Supported Tags

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

## Groups Tag
**Mandatory**: no
**Since**: 13.0.0
It contains the names of the Groups that the app belongs (comma separated). Groups are available since WebSite X5 v13.

```xml
<Groups>Animation, Button</Groups>
```

## InitialSize Tag
**Mandatory**: no
**Since**: 13.0.1
It contains the sizes ([width],[height]) that the object will assume when it will be created as template object.

```xml
<InitialSize>200,150</InitialSize>
```

## MinRecommendedSize Tag
**Mandatory**: no
**Since**: 13.0.1
It contains the sizes ([width],[height]) under which the object is not displayed properly.

```xml
<MinRecommendedSize>100,50</MinRecommendedSize>
```

## MinimumSize Tag
**Mandatory**: no
**Since**: 13.0.1
It contains the limit sizes ([width],[height]) of the object.

```xml
<MinimumSize>50,50</MinimumSize>
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
|shared|no|`false`|If set to "true" the resource will be copied only once in a shared folder for all objects of this type. This will allow to avoid duplicated copies of a static file. If `action="process"`, this flag will be ignored. |
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

## Admin Tag
**Mandatory**: no
**Since**: 15.2.0

Using this tag you can specify a resource that is used as content of an admin section or as content of a dashboard box.
In the `Admin` tag, you should specify one `Pages` tag and/or a `Dashboard` tag.

### Pages tag

This tag allow you to add a new section to the admin area of the site.

It shall contain one or more `Page` tag.
The `Page` tag should specify a `resource-id` attribute that contains the id of the [Resource](#resources-tag) loaded in the admin section.

Only one entry in the menu will be made if the specified resource is shared and set as `action="copy"`. The link is valid for all the optional objects of the same kind. If the resource is not shared, there will be an entry for each optional object.

The content of the specified resource will be [included](http://php.net/manual/en/function.include.php) in a PHP file of the admin section. A link to it will be automatically added to the "admin" section of the online site.

Optionally, you can specify the icon resource id using the `icon-resource-id` attribute. The icon is used in the side menu of the admin section of the site.

The `Page` tag should contain a `Title` tag that should contain the title of the specified section. It can be localized using the l10-id attribute.

### Dashboard tag

This tag allow you to add a new box to the admin dashboard.

It shall contain one or more `Box` tag.
The `Box` tag should specify a `resource-id` attribute that contains the id of the [Resource](#resources-tag) loaded in the admin section.

Only one box will be shown if the specified resource is shared and set as `action="copy"`. The box is valid for all the optional objects of the same kind. If the resource is not shared, there will be a box for each optional object.

The content of the specified resource will be [included](http://php.net/manual/en/function.include.php) in a PHP file of the admin section. A link to it will be automatically added to the "admin" section of the online site.

Optionally, you can specify the icon resource id using the `icon-resource-id` attribute. The icon is used in the side menu of the admin section of the site.

The `Box` tag should contain a `Title` tag that should contain the title of the specified section. It can be localized using the l10-id attribute.

```xml
<!-- Define the resources using the Resources tag -->
<Resources>
	<Resource id="admin" src="admin.php" />
	<Resource id="admin-dash" src="admin.php" />
	<Resource id="admin-icon" src="icon.png" />
</Resources>
<!-- Then use the resources ids to define the admin sections and boxes -->
<Admin>
	<Pages>
		<Page resource-id="admin" icon-resource-id="admin-icon">
			<Title l10n-id="title">This is the menu entry title</Title>
		</Page>
	</Pages>
	<Dashboard>
		<Box resource-id="admin-dash" icon-resource-id="admin-icon">
			<Title l10n-id="title">This is the dashboard box title</Title>
		</Box>
	</Dashboard>
</Admin>
```

## Includes Tag
**Mandatory**: no
**Since**: 15.2.0
You can include multiple libraries to the WSX5Script code by using this include tag.
The code you specify using this tag will be executed as WSX5Script before any other code is executed.

```xml
<!-- This example includes an external library and some custom inline code -->
<Includes>
	<Include src="includes/library1.js" />
	<Include>
		// You can type some JS code in here too
		var thisIsInline = true;
	</Include>
</Includes>
```

## Dependencies Tag
**Mandatory**: no
Using this tag you can specify the dependency of your Optional Object from a WebSite X5 component.
Extra data will be available inside the WSX5Script depending on the specified dependencies.
This tag must contain one or more of the following subtags:

### BasicElements
Set the content of this subtag to `true` if your Optional Object reads the basic website data.
If no dependency is set, then this is automatically included. If you specify one or more dependency, this is included only if specified as dependency.

### AccessManagement
Set the content of this subtag to `true` if your Optional Object reads data set in the Access Management section at step 4. In this case, the object is rebuilt whenever the user changes the Access Management settings.

### DataManagement
Set the content of this subtag to `true` if your Optional Object reads data set in the Data Management section at step 4. In this case, the object is rebuilt whenever the user changes the Data Management settings.

### ShoppingCart
Set the content of this subtag to `true` if your Optional Object reads the basic data set in the Shopping Cart section at step 4. In this case, the object is rebuilt whenever the user changes the Shopping Cart settings.

### ShoppingCartProducts
Set the content of this subtag to `true` if your Optional Object reads the products data set in the Shopping Cart section at step 4. In this case, the object is rebuilt whenever the user changes the Shopping Cart settings.

### ShoppingCartPayments
Set the content of this subtag to `true` if your Optional Object reads the payments data set in the Shopping Cart section at step 4. In this case, the object is rebuilt whenever the user changes the Shopping Cart settings.

### ShoppingCartShippings
Set the content of this subtag to `true` if your Optional Object reads the shippings data set in the Shopping Cart section at step 4. In this case, the object is rebuilt whenever the user changes the Shopping Cart settings.

### Blog
Set the content of this subtag to `true` if your Optional Object reads data set in the Blog section at step 4. In this case, the object is rebuilt whenever the user changes the Blog settings.

### RSSFeed
Set the content of this subtag to `true` if your Optional Object reads data set in the RSS Feed section at step 4. In this case, the object is rebuilt whenever the user changes the RSS Feed settings.

### ModelStyle
Set the content of this subtag to `true` if your Optional Object reads model style data set in the Text, Field and Button Style section at step 2. In this case, the object is rebuilt whenever the user changes the model style settings.

### SiteElements
Set the content of this subtag to `true` if your Optional Object reads the site structur data set in the Map Creation section at step 2. In this case, the object is rebuilt whenever the user changes the site structure.

In the following example, the Optional Object is rebuilt when the user changes something in the Access Management section of WebSite X5.
```xml
<Dependencies>
	<AccessManagement>true</AccessManagement>
</Dependencies>
```

## ShowPreview Tag
**Mandatory**: no
If set to `true`, the UI of WebSite X5 will show a preview of the object directly in the window where the input fields are available.

## Overflow Tag
**Mandatory**: no
**Since**: 12.0.0
Set to `true` to set the CSS overflow to `visible` in the cell format. This allows the Optional Object's content to exit from its cell.

## Output Tag
**Mandatory**: yes
This tag contains the code which has to be used to create the HTML code to insert inside the site page.
This tag may contain any kind of code. It will be then copied inside the code of the page.
Inside this tag you can write [WSX5 Script](wsx5-script.md) code. It must be executed within the `<?wsx5` and `?>` tag. This code follows the guidelines described in the [WSX5 Script](wsx5-script.md) section.

This tag supports the loading of contents from external files. See [this paragraph to get more information](#loading-of-external-content-in-the-manifest)

## PreviewOutput Tag
**Mandatory**: no
If available, it contains the output HTML code to show in the small preview present in the editor of the page or in the editor of the template when the object is selected. Works like the Output tag.

This tag supports the loading of contents from external files. See [this paragraph to get more information](#loading-of-external-content-in-the-manifest)

## UIPreviewOutput Tag
**Mandatory**: no
If available, it contains the output HTML code to show in the preview present during the editing of the object. Works like the Output tag.

This tag supports the loading of contents from external files. See [this paragraph to get more information](#loading-of-external-content-in-the-manifest)
