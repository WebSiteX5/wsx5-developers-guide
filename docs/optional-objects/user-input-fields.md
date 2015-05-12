# Fields Tag

The Field tag must contains a list of Field tag which are the input fields visible to the user in the UI of WebSite X5.

Each Field tag needs to have an unique id defined using the "id" attribute.

Every "Field" tag can contain:

* The **type** attribute: which defines the type of field according to the list you will find below.
* a **Label** subtag: defines the label shown near the field. This tag can have the attribute "position" with as values "top", "left" or "none". 
* a **Mandatory** subtag: set to true to set the field as mandatory
* The **UpdatesPreview** subtag which, if set as true, will update automatically the preview with every change in the UI. As default it is set as false.
* A **Hooks** subtag where following JS functions can be defined (without need of the use of the tags <?wsx5 ?>):
    * OnCreate(): Is called before generating the field. The output of this function will be used to generate the field contents. Note: at the moment only the dropdown field actually uses this function.
    * OnValueChanged(): Is called when the user changes the value of this field in the UI of WebSite X5.
* The **Description** subtag which can be localized via the attributes l10n-id and global-l10n-id, with the description of the field. It can have the attribute "style" where the value can be "normal" (default) or "info".
* An **Indent** subtag with a numerical integer value bigger or equal to zero. It indicates the indent level of the field according to the left border of the form.
* A **Position** subtag with the word "auto" or an integer value bigger or equal to zero. In case it contains "auto" the fields will be positionend automatically. In case it contains an integer value the field will be positioned in the same position of the field indicated by the value.

Here you can find a list of the available field types.
The values represented in the following XML code examples are not to consider as default values for the various fields.
## Text
Show a text input.
### XML code supported in manifest
```xml
<Field type="text" id="">
  <DefaultValue>DefaultValue</DefaultValue>
  <IsPassword>false</IsPassword>
  <ShowPasswordCreation>false</ShowPasswordCreation>
  <MaxLength>10</MaxLength>
  <MultiLine>false</MultiLine>
  <LinesCount>1</LinesCount>
  <ShowScrollbar>false</ShowScrollbar>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript code
* value (string)

## Number
Allows to choose a number
### XML code supported in manifest
```xml
<Field type="number" id="">
<DefaultValue>10</DefaultValue>
<MinValue>0</MinValue>
<MaxValue>100</MaxValue>
<Increment>5</Increment>
<ShowDecimals>false</ShowDecimals>
<Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript code
* value (number)

## Color
Allows to choose a color from a palette.
### XML code supported in manifest
```xml
<Field type="color" id="">
  <EnableTransparent>false</EnableTransparent>
	<DefaultValue>(#AARRGGBB|#RRGGBB)</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript code
* value (hexadecimal string)
* valueR (integer 0-255)
* valueG (integer 0-255)
* valueB (integer 0-255)
* valueA (integer 0-255)

## Colors
Allows to choose four colors.
### XML code supported in manifest
```xml
<Field type="colors" id="">
  <EnableTransparent>false</EnableTransparent>
  <DefaultValue>(#AARRGGBB|#RRGGBB)</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript code
* top (hexadecimal string)
* bottom (hexadecimal string)
* left (hexadecimal string)
* right (hexadecimal string)
* leftR (integer 0-255)
* leftG (integer 0-255)
* leftB (integer 0-255)
* leftA (integer 0-255)
* rightR (integer 0-255)
* rightG (integer 0-255)
* rightB (integer 0-255)
* rightA (integer 0-255)
* topR (integer 0-255)
* topG (integer 0-255)
* topB (integer 0-255)
* topA (integer 0-255)
* bottomR (integer 0-255)
* bottomG (integer 0-255)
* bottomB (integer 0-255)
* bottomA (integer 0-255)

## BorderWidth
Allows to choose the width of 4 borders.
### XML code supported in manifest
```xml
<Field type="borderwidth" id="">
  <DefaultValue>1</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript code
* left (integer)
* right (integer)
* top (integer)
* bottom (integer)

## RoundCorners
Allows to choose the rounding of the corners.
### XML code supported in manifest
```xml
<Field type="roundcorners" id="">
  <DefaultValue>1</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* topLeft (integer)
* topRight (integer)
* bottomLeft (integer)
* bottomRight (integer)

## Shadow
Allows to choose the style of a shadow.
### XML code supported in manifest
```xml
<Field type="shadow" id="">
  <DefaultEnabled>false</DefaultEnabled>
  <DefaultColor>(#AARRGGBB|#RRGGBB)</DefaultColor>
  <DefaultOffsetX>1</DefaultOffsetX>
  <DefaultOffsetY>1</DefaultOffsetY>
  <DefaultDimension>10</DefaultDimension>
  <DefaultDiffusion>10</DefaultDiffusion>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
*  enabled
*  color (hexadecimal string)
*  colorR (integer 0-255)
*  colorG (integer 0-255)
*  colorB (integer 0-255)
*  colorA (integer 0-255)
*  diffusion (integer)
*  dimension (integer)

## Dimensions
Allows to choose width and height using a single UI control.
### XML code supported in manifest
```xml
<Field type="dimensions" id="">
  <DefaultValue>100</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <KeepRatio>true</KeepRatio>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* width
* height

## Margins
Allows to choose 4 margins.
### XML code supported in manifest
```xml
<Field type="margins" id="">
  <DefaultValue>1</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* top (integer)
* bottom (integer)
* left (integer)
* right (integer)

## Checkbox
Allows to create a check box.
### XML code supported in manifest
```xml
<Field type="checkbox" id="">
  <DefaultChecked>true</DefaultChecked>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
checked (Boolean)
## Separator
Allows to add a separator. A separator can change the behavior of a panel (column) inside the UI of the application. 
It can have a sub tag NewPanel which, if it contains "true" this forces the creation of a new section in a new panel.
### XML code supported in manifest
```xml
<Field type="separator" id="">
  <Label l10n-id="loc_id">Default label text</Label>
  <NewPanel>true</NewPanel>
</Field>
```

## Dropdown
It is a field which is represented like a drop down menu.
If a class is defined with the attribute "class" then it will be filled automatically by webSite X5 based on the class value. 
the available class values are the follwing:
database: shows a dropdown menu to select a database defined in step 4 
### XML code supported in manifest
```xml
<Field type="dropdown" id="" shownumbers="(true|false)" class="database">
	<Options>
		<Option l10n-id="localization_id" value="field_value">Default text</Option>
	</Options>
  <Hooks><![CDATA[
    function OnCreate() {
      // Must return the options array.
      // Each option element is defined via a JSON object
      // containing a text and a value property.
      return [{ text: "option text", value: "option value" }];
    }
    ]]>
  </Hooks>
	<DefaultValue>value_default_option</DefaultValue>
<Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
value (string)
## Font
It is a field which allows to choose the font, it's size and style.
### XML code supported in manifest
```xml
<Field type="font" id="">
  <DefaultFontFamily>Tahoma</DefaultFontFamily>
  <DefaultFontSize>10</DefaultFontSize>
  <DefaultBold>false</DefaultBold>
  <DefaultItalic>false</DefaultItalic>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* family (string)
* size (integer pt)
* bold (Boolean)
* italic (Boolean)

## FileList
Allows to choose a list of files.
### XML code supported in manifest
```xml
<Field type="filelist" id="">
  <Extensions>jpg,txt</Extensions>
  <AllowUrls>true</AllowUrls>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* list (array of FileSelect elements)
* list.lenght (number of elements in the array)
* list.path (path for the file example list[0].path prints the path of the first file)

## StringList
Allows to add a list of strings.
### XML code supported in manifest
```xml
<Field type="stringlist" id="">
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* list (strings array)

## File
Allows to choose a file.
### XML code supported in manifest
```xml
<Field type="file" id="">
  <Extensions>jpg,txt</Extensions>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Properties accessible via JavaScript
* path (string)
* name (string)
* extension
* isImage (Boolean)
* isUrl (Boolean)
* width: only if `isImage == true`
* height: only if `isImage == true`
* clones: only if `isImage == true`. Contains the list of clones of the image. Everyone has the fields shown above.

## Link
Allows to choose a link from the link selection window of WebSite X5.
### XML code supported in manifest
```xml
<Field type="link" id="">
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
### Methods accessible via JavaScript code
* getHTML(string content)
