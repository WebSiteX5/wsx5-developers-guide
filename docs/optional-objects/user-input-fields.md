# Fields Tag

The Field tag must contains a list of Field tag which are the input fields visible to the user in the UI of WebSite X5.
Each Field tag needs to have an unique id defined using the `id` attribute.

Each `Field` tag can have the following properties:

|Property Name| Mandatory | Description                                                                                            |
|-------------|-----------|--------------------------------------------------------------------------------------------------------|
| id          | yes       | The id that identifies the field in the [WSX5 Script](wsx5-script.md)                                  |
| type        | yes       | Defines the type of field according to the list you will find below ("text", "number", "dropdown", ...)|

Each `Field` tag can have the following subtags:

| Subtag name    | Mandatory    | Default Value | Description |
|----------------|--------------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Description    | no           | (empty)       | It can have the attribute `style` where the value can be "normal" (default) or "info". Can be localized via the attributes `l10n-id` and `global-l10n-id`.                                          |
| Enabled        | no           | `true`        | Set to `false` to disable this field. It will be shown but its contents won't be editable.                                                                                                          |
| Hooks          | no           | (empty)       | [See below](#hooks-subtag).                                                                                                                                                                         |
| Indent         | no           | 0             | Indicates the indent level of the field according to the left border of the form. Must have a numerical integer value bigger or equal to zero. Since v2019.1 we recommend setting it 2 in 2.                                                      |
| Label          | no           | (empty)       | [See below](#label-subtag).       |
| Mandatory      | no           | `false`       | Set to `true` to set the field as mandatory.                                                                                                                                                        |
| Position       | no           | "auto"        | In case it contains "auto" the fields will be positionend automatically. In case it contains an integer value the field will be positioned in the same position of the field indicated by the value.|
| UpdatesPreview | no           | `false`       | Set to `true` to automatically update the preview when the value of this field is changed.                                                                                                          |
| Visible        | no           | `true`        | Set to `false` to hide this field.                                                                                                                                                                  |

### Hooks Subtag
The **Hooks** subtag can contain a set of JavaScript functions that must be defined without using the
`<?wsx5` and `?>` tags. That is, the field contains pure [WSX5 Script](wsx5-script.md) code.
You can define the following functions:

**OnCreate()**
It's called before generating the field. The output of this function will be used to generate the field contents.
**Note**: at the moment only the [dropdown](#dropdown) field actually uses this function.

**OnValueChanged()**
It is called when the user changes the value of this field in the UI of WebSite X5. The output of this function will be used to [dynamically update fields values](dynamic-update-fields.md).

**OnSelectionChanged(indexes, keys, values)**
It is called when the user changes the selection of this stringlist field in the UI of WebSite X5. The output of this function will be used to [dynamically update fields values](dynamic-update-fields.md).

| Argument name | Type             | Notes                    |
|---------------|------------------|--------------------------|
| indexes       | Array of Integer | List of selected indexes |
| keys          | Array of String  | List of selected keys    |
| values        | Array of String  | List of selected values  |

### Label Subtag
The **Label** subtag defines the label shown near the field. This tag can have:<br />- The `position` attribute with values "top", "left" or "none".<br />- The `width` attribute (since v11.0.8 to last v17) that must contain a number. The attribute is deprecated, however you can continue to use to configure the UI for versions <= v17.<br />- The `widthV2` attribute (since v2019.1) that is the new reference for the width (the `independentWidthAuto` must be false).<br />- The `independentWidthAuto` attribute (since v2019.1), if set to true the width will be calculated by the imInputControl control. The default is false.<br /><br />**Note**:<br />Since v2019.1 the label width will be calculated automatically from WSX5, section by section (from separator to separator): the width for each section will be the largest of the section's labels. (only those with positioning on the left). Labels with attributes `widthV2` and `independentWidthAuto` are not considered.



# Available field types

Here you can find a list of the available field types.
The values represented in the following XML code examples are not to consider as default values for the various fields.

## Borders
Available since v2024.1
Allows to specify all the borders properties, that is color, width, round corners and shadow, with UI controls positioned in the same line and with a single label. It's possible to show only a subset of that properties.
`Width`, `Color`, `RoundCorners` and `Shadow` are defined like the corresponding stand-alone fields, except for the absence of `Label` and other general subtags (`Enabled`, `Visible`, ...), that applies only to whole borders field.
`Id` attribute must be specified for each of those elements, but can be left empty.

**Complete list of subtags**
```xml
<Field type="borders" id="field-id">
  <ShowWidth>true</ShowWidth>
  <ShowColor>true</ShowColor>
  <ShowRoundCorners>true</ShowRoundCorners>
  <ShowShadow>true</ShowShadow>
  <Width id="">
    <DefaultValue>1,2,3,4</DefaultValue>
    <MinValue>0</MinValue>
    <MaxValue>20</MaxValue>
    <Increment>3</Increment>
  </Width>
  <Color id="">
    <EnableTransparent>true</EnableTransparent>
    <DefaultValue>#FFFF00</DefaultValue>
  </Color>
  <RoundCorners id="">
    <DefaultValue>1</DefaultValue>
    <MinValue>0</MinValue>
    <MaxValue>100</MaxValue>
    <Increment>5</Increment>
  </RoundCorners>
  <Shadow id="">
    <DefaultEnabled>true</DefaultEnabled>
    <DefaultColor>#000000</DefaultColor>
    <DefaultOffsetX>1</DefaultOffsetX>
    <DefaultOffsetY>1</DefaultOffsetY>
    <DefaultDimension>10</DefaultDimension>
    <DefaultDiffusion>10</DefaultDiffusion>
    <ShowSpread>true</ShowSpread>
  </Shadow>
  <Label l10n-id="loc_id">Bordi</Label>
  <UpdatesPreview>true</UpdatesPreview>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].borderWidth; // CSS string like "1px 2px 3px 4px"
var value = parameters['field-id'].borderColor; // CSS string like "rgba(255, 255, 0, 1) rgba(255, 255, 0, 1) rgba(255, 255, 0, 1) rgba(255, 255, 0, 1)"
var value = parameters['field-id'].borderRadius; // CSS string like "1px 2px 3px 4px"
var value = parameters['field-id'].boxShadow; // CSS string like "1px 1px 10px 10px rgba(0, 0, 0, 1)"
var value = parameters['field-id'].borderWidthCSS; // CSS string like "border-block-width: 1px 2px; border-inline-width: 3px 4px; "
var value = parameters['field-id'].borderColorCSS; // CSS string like "border-block-color: rgba(255, 255, 0, 1) rgba(255, 255, 0, 1); border-inline-color: rgba(255, 255, 0, 1) rgba(255, 255, 0, 1); "
var value = parameters['field-id'].borderRadiusCSS; // CSS string like "border-start-start-radius: 1px; border-start-end-radius: 2px; border-end-start-radius: 3px; border-end-end-radius: 4px; "

var value = parameters['field-id'].width.left; // integer
var value = parameters['field-id'].width.right; // integer
var value = parameters['field-id'].width.top; // integer
var value = parameters['field-id'].width.bottom; // integer
var value = parameters['field-id'].width.leftCSS; // CSS string like "border-inline-start-width: 1px; "
var value = parameters['field-id'].width.rightCSS; // CSS string like "border-inline-end-width: 1px; "
var value = parameters['field-id'].width.CSS; // CSS string like "border-block-width: 1px 2px; border-inline-width: 3px 4px; "

var value = parameters['field-id'].color.top; // CSS string like "#45ff23"
var value = parameters['field-id'].color.bottom; // CSS string like "#45ff23"
var value = parameters['field-id'].color.left; // CSS string like "#45ff23"
var value = parameters['field-id'].color.right; // CSS string like "#45ff23"
var value = parameters['field-id'].color.leftCSS; // CSS string like "border-inline-start-color: #45ff23; "
var value = parameters['field-id'].color.rightCSS; // CSS string like "border-inline-end-color: #45ff23; "
var value = parameters['field-id'].color.CSS; // CSS string like "border-block-color: #45ff23 #45ff23; border-inline-color: #45ff23 #45ff23; "

var value = parameters['field-id'].roundCorners.topleft; // integer
var value = parameters['field-id'].roundCorners.topright; // integer
var value = parameters['field-id'].roundCorners.bottomleft; // integer
var value = parameters['field-id'].roundCorners.bottomright; // integer
var value = parameters['field-id'].roundCorners.topleftCSS; // CSS string like "border-start-start-radius: 1px; "
var value = parameters['field-id'].roundCorners.toprightCSS; // CSS string like "border-start-end-radius: 1px; "
var value = parameters['field-id'].roundCorners.bottomleftCSS; // CSS string like "border-end-start-radius: 1px; "
var value = parameters['field-id'].roundCorners.bottomrightCSS; // CSS string like "border-end-end-radius: 1px; "
var value = parameters['field-id'].roundCorners.CSS; // CSS string like "border-start-start-radius: 1px; border-start-end-radius: 2px; border-end-start-radius: 3px; border-end-end-radius: 4px; "

var value = parameters['field-id'].shadow.active; // true if the 'enable' checkbox is checked
var value = parameters['field-id'].shadow.color (hexadecimal string);
var value = parameters['field-id'].shadow.colorR (integer 0-255);
var value = parameters['field-id'].shadow.colorG (integer 0-255);
var value = parameters['field-id'].shadow.colorB (integer 0-255);
var value = parameters['field-id'].shadow.colorA (integer 0-255);
var value = parameters['field-id'].shadow.offsetX (integer);
var value = parameters['field-id'].shadow.offsetY (integer);
var value = parameters['field-id'].shadow.blur (integer); // Dimension value
var value = parameters['field-id'].shadow.spread (integer); // Diffusion value
var value = parameters['field-id'].shadow.showSpread (bool); // Diffusion enabled
```

## BorderWidth
Allows to choose the width of 4 borders. `DefaultValue` can contains up to 4 comma separated values, with the same meaning as CSS syntax:
- 1 value: all four sides
- 2 values: top and bottom | left and right
- 3 values: top | left and right | bottom
- 4 values: top | right | bottom | left

**Complete list of subtags**
```xml
<Field type="borderwidth" id="field-id">
  <DefaultValue>1</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].left; // integer
var value = parameters['field-id'].right; // integer
var value = parameters['field-id'].top; // integer
var value = parameters['field-id'].bottom; // integer
var value = parameters['field-id'].leftCSS; // CSS string like "border-inline-start-width: 1px; "
var value = parameters['field-id'].rightCSS; // CSS string like "border-inline-end-width: 1px; "
var value = parameters['field-id'].CSS; // CSS string like "border-block-width: 1px 2px; border-inline-width: 3px 4px; "
```

## Checkbox
Allows to create a check box.

**Complete list of subtags**
```xml
<Field type="checkbox" id="">
  <DefaultChecked>true</DefaultChecked>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].checked // Boolean
```

## Color
Allows to choose a color from a palette.

**Complete list of subtags**
```xml
<Field type="color" id="">
  <EnableTransparent>false</EnableTransparent>
  <ShowOpacity>true</ShowOpacity> <!-- Available since v2024.1 -->
  <DefaultValue>(#AARRGGBB|#RRGGBB)</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].value; // CSS string like "rgba(153, 127, 83, 0.87)"
var redValue = parameters['field-id'].valueR; // Number 0-255
var greenValue = parameters['field-id'].valueG; // Number 0-255
var blueValue = parameters['field-id'].valueB; // Number 0-255
var alphaValue = parameters['field-id'].valueA; // Number 0-255
```

## Colors
Allows to choose four colors.
**Complete list of subtags**

```xml
<Field type="colors" id="">
  <EnableTransparent>false</EnableTransparent>
  <DefaultValue>(#AARRGGBB|#RRGGBB)</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var top = parameters['field-id'].top; // CSS string like "#45ff23"
var bottom = parameters['field-id'].bottom; // CSS string like "#45ff23"
var left = parameters['field-id'].left; // CSS string like "#45ff23"
var right = parameters['field-id'].right; // CSS string like "#45ff23"
var leftRed = parameters['field-id'].leftR; // integer 0-255
var leftGreen = parameters['field-id'].leftG; // integer 0-255
var LeftBlue = parameters['field-id'].leftB; // integer 0-255
var leftAlpha = parameters['field-id'].leftA; // integer 0-255
var rightRed = parameters['field-id'].rightR; // integer 0-255
var rightBlue = parameters['field-id'].rightG; // integer 0-255
var rightGreen = parameters['field-id'].rightB; // integer 0-255
var rightAlpha = parameters['field-id'].rightA; // integer 0-255
var topRed = parameters['field-id'].topR; // integer 0-255
var topBlue = parameters['field-id'].topG; // integer 0-255
var topGreen = parameters['field-id'].topB; // integer 0-255
var topAlpha = parameters['field-id'].topA; // integer 0-255
var bottomRed = parameters['field-id'].bottomR; // integer 0-255
var bottomBlue = parameters['field-id'].bottomG; // integer 0-255
var bottomGreen = parameters['field-id'].bottomB; // integer 0-255
var bottomAlpha = parameters['field-id'].bottomA; // integer 0-255
var leftCSS = parameters['field-id'].leftCSS; // CSS string like "border-inline-start-color: #45ff23; "
var rightCSS = parameters['field-id'].rightCSS; // CSS string like "border-inline-end-color: #45ff23; "
var CSS = parameters['field-id'].CSS; // CSS string like "border-block-color: #45ff23 #45ff23; border-inline-color: #45ff23 #45ff23; "
```

## DateTime
Available since v2024.1
Allows to choose a date (and a time, if `<ShowTime>true</ShowTime>`; default is false).

**Complete list of subtags**
```xml
<Field type="datetime" id="">
  <DefaultValue>2023-11-22T15:30:00</DefaultValue>
  <ShowTime>true</ShowTime>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var dateTimeValue = parameters['field-id'].value; // Date JS object
```

## Dimensions
Allows to choose width and height using a single UI control.

**Complete list of subtags**
```xml
<Field type="dimensions" id="">
  <DefaultValue>100</DefaultValue>
  <DefaultWidthValue>100</DefaultWidthValue><!-- Available since v12.0.2 -->
  <DefaultHeightValue>100</DefaultHeightValue><!-- Available since v12.0.2 -->
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <KeepRatio>true</KeepRatio>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
**Note**
To provide maximum compatibility with versions older than 12.0.2, if you need to specify a default value for this field you should always provide both the old `<DefaultValue>` and the new
`<DefaultWidthValue>` / `<DefaultHeightValue>` fields.
If you only provide the new tags, older WSX5 versions won't thrown any error but the default value will not be provided.

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].width; // integer
var value = parameters['field-id'].height; // integer
```

## Dropdown
It shows a drop down menu.
If a class is defined using the `class` attribute then it will be filled automatically by webSite X5 based on the class value. 
At the moment, only the **database** class is available. It shows a dropdown menu to select a database that was previously defined by the user at step 4 of WebSite X5.

**Complete list of subtags**
To see how to use this field see the examples below.
```xml
<Field type="dropdown" id="" class="database">
  <ShowNumbers>true</ShowNumbers>
  <DefaultValue>value_default_option</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
  <!-- Use the Options OR the Hooks tag. Do not use them both -->
  <Options>
    <Option l10n-id="localization_id" value="field_value" icon="icon_path">Default text</Option>
  </Options>
  <Hooks><![CDATA[
    function OnCreate() {
      // Must return the options array.
      // Each option element is defined via a JSON object
      // containing a text, a value and an icon property.
      return [{ text: "option text", value: "option value", icon: "icon_path" }];
    }
    ]]>
  </Hooks>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].value; // String
```
### Examples

**How to add more options using the `<Options>` tag**
```xml
<Field type="dropdown" id="" class="database">
  <Options>
    <Option l10n-id="loc_id_1" value="value_1">default text 1</Option>
    <Option l10n-id="loc_id_2" value="value_2" icon="icon_2.jpg">default text 2</Option>
    <Option l10n-id="loc_id_3" value="value_3">default text 3</Option>
    <Option l10n-id="loc_id_4" value="value_4">default text 4</Option>
  </Options>
  <Label l10n-id="label-id">Default Label</Label>
</Field>
```

**How to add more options using the `<Hooks>` tag**
Note that if you use this tag, you should not use the `<Options>` tag.
```xml
<Field type="dropdown" id="" class="database">
  <Label l10n-id="label-id">Default Label</Label>
  <Hooks>
    <![CDATA[
    function OnCreate() {
      return [{ text: "option text", value: "option value" }];
    }
    ]]>
  </Hooks>
</Field>
```

**How to create a list of available databases**
In the following example, the dropdown list is filled with the databases set at Step 4 of WebSite X5.

```xml
<Field type="dropdown" id="" class="database">
  <Label l10n-id="db-localization-id">Select the database:</Label>
</Field>
```

## File
Allows to choose a file.

**Complete list of subtags**
```xml
<Field type="file" id="">
  <Extensions>jpg,txt</Extensions>
  <!-- If set to true it allow using of PixaBay Images, false is the default: for fields that don't use images input don't use this tag -->
  <ShowOnlineLibrary>false</ShowOnlineLibrary> <!-- Deprecated: 2022.2.0.0 -->
  <ShowOnlineImageLibrary>false</ShowOnlineImageLibrary> <!-- Since: 2022.2.0.0 -->
  <ShowOnlineVideoLibrary>false</ShowOnlineVideoLibrary> <!-- Since: 2022.2.0.0 -->
  <ShowAccessibility>true</ShowAccessibility> <!-- Since: 2025.1.0.0; if true, the UI shows the accessibility icon, that opens a popup to insert alternative text and title for each file or, alternatively, to mark the file as decorative -->
  <IsDecorativeAsDefault>true</IsDecorativeAsDefault> <!-- Since: 2025.1.0.0; if true, as soon as a file is selected, it's marked as decorative; the user can always mark it as non-decorative and set alternative text and title -->
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].path; // String
var value = parameters['field-id'].alt; // String; don't access this field directly; use a11y.generateAccessibilityPropsHTML() or a11y.getAlt() instead
var value = parameters['field-id'].title; // String; don't access this field directly; use a11y.generateAccessibilityPropsHTML() or a11y.getTitle() instead
var value = parameters['field-id'].isDecorative; // Boolean
var value = parameters['field-id'].name; // String
var value = parameters['field-id'].extension; // String
var value = parameters['field-id'].isImage; // Boolean
var value = parameters['field-id'].isUrl; // Boolean
var value = parameters['field-id'].width; // only if `isImage == true`
var value = parameters['field-id'].height; // only if `isImage == true`
var value = parameters['field-id'].fullWidth; //Boolean
var value = parameters['field-id'].clones; // only if `isImage == true`. Contains the list of clones of the image. Everyone has the fields shown above.
```

## FileList
Allows to choose a list of files.

**Complete list of subtags**
```xml
<Field type="filelist" id="">
  <Extensions>jpg,txt</Extensions>
  <AllowUrls>true</AllowUrls>
  <!-- If set to true it allow using of PixaBay Images, false is the default: for fields that don't use images input don't use this tag -->
  <ShowOnlineImageLibrary>false</ShowOnlineImageLibrary> <!-- Since: 2022.2.0.0 -->
  <ShowOnlineVideoLibrary>false</ShowOnlineVideoLibrary> <!-- Since: 2022.2.0.0 -->
  <ShowAccessibility>true</ShowAccessibility> <!-- Since: 2025.1.0.0; if true, the UI shows the accessibility icon, that opens a popup to insert alternative text and title for each file or, alternatively, to mark the file as decorative -->
  <IsDecorativeAsDefault>true</IsDecorativeAsDefault> <!-- Since: 2025.1.0.0; if true, as soon as a file is selected, it's marked as decorative; the user can always mark it as non-decorative and set alternative text and title -->
  <Label l10n-id="loc_id">Default label text</Label>
  <DescriptionEnabled>false</DescriptionEnabled>
  <AltTitleEnabled>false</AltTitleEnabled> <!-- Since: 2023.1.4.0; deprecated in 2025.1.0.0, replaced by ShowAccessibility -->
  <LinkEnabled>false</LinkEnabled>
  <ElementList>false</ElementList> <!-- Since: 2023.1.4.0 -->
  <Height>255</Height> <!-- Since: 2023.1.5.0 -->
  <!-- Small and medium thumb size toolbar buttons are always visible; large thumb size toolbar button is visible only if ShowLargeThumbs = true -->
  <ShowLargeThumbs>true</ShowLargeThumbs> <!-- Since: 2024.1.2.0 -->
  <!-- Default selected thumb size toolbar button; allowed values: Small, Medium and Large (only if ShowLargeThumbs = true) -->
  <DefaultThumbSize>Small</DefaultThumbSize> <!-- Since: 2024.1.2.0 -->
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].list; // (array of FileSelect elements)
var value = parameters['field-id'].list.length; // (number of elements in the array)
var value = parameters['field-id'].list[index]; // (File at specified index, it contains same data of <Field type="file">. list[0] is the first file, list[list.length-1] is the last one)
```

## Font
It is a field which allows to choose the font, it's size and style.

**Complete list of subtags**
```xml
<Field type="font" id="">
  <DefaultFont>true</DefaultFont>
  <DefaultFontFamily>Tahoma</DefaultFontFamily>
  <DefaultFontSize>10</DefaultFontSize>
  <DefaultBold>false</DefaultBold>
  <DefaultItalic>false</DefaultItalic>
  <ShowBold>true</ShowBold>
  <ShowItalic>true</ShowItalic>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].defaultFamily; // Boolean
var value = parameters['field-id'].family; // string
var value = parameters['field-id'].size; // integer pt
var value = parameters['field-id'].bold; // Boolean
var value = parameters['field-id'].italic; // Boolean
```


## ImageSelect
Available since v13.1.5.16
It is a field which allows to choose from a list of images shown in a dropdown

**Complete list of subtags**
```xml
<Field type="imageselect" id="">
    <LibraryFolder>folder/subfolder</LibraryFolder> <!-- The relative path of the folder (inside Resources folder) that contains the list of images -->
    <LibraryImageWidth>22</LibraryImageWidth>
    <LibraryImageHeight>22</LibraryImageHeight>
    <AllowCustomImage>false</AllowCustomImage> <!-- If true the user can select a custom image from file select dialog -->
    <AcceptedExtensions>*.png</AcceptedExtensions> <!-- The allowed extensions of the sfile select dialog -->
    <DefaultIndex>0</DefaultIndex> <!-- The default selected image -->
    <Label l10n-id="loc_id">Default label text</Label>
	<ShowAccessibility>true</ShowAccessibility> <!-- Since: 2025.1.0.0; if true, the UI shows the accessibility icon, that opens a popup to insert alternative text and title for each file or, alternatively, to mark the file as decorative -->
	<IsDecorativeAsDefault>true</IsDecorativeAsDefault> <!-- Since: 2025.1.0.0; if true, as soon as a file is selected, it's marked as decorative; the user can always mark it as non-decorative and set alternative text and title -->
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].selectedIndex; // The selected index. -1 if custom image is selected 
var value = parameters['field-id'].file; // Selected file element, it contains same data of <Field type="file">.
```

## Link
Allows to choose a link from the link selection window of WebSite X5.

**Complete list of subtags**
```xml
<Field type="link" id="">
  <Label l10n-id="loc_id">Default label text</Label>
  <DisableFileLinks>false</DisableFileLinks>
  <DisableTooltip>false</DisableTooltip>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
// "raw" property conteins raw link data. It is available if DisableFileLinks and DisableTooltip are set to true
var rawLink = parameters['field-id'].raw;

// "getHTML" method return text given wrapped by tag "a", if link was specified, otherwise only text given.
var value = parameters['field-id'].getHTML("link text html"); // String

// Example of use
if (parameters['field-id'].getHTML("#link#") != "#link#") { // link was specified
    document.write(parameters['field-id'].getHTML("link text html")); // <a href="[link value]">link text html</a>
} else {...} // link wasn't specified

// "getHTMLStartEnd" method return an array of 2 elements: the opening and closing tags of link, if is was specified,
// otherwise an array with 2 empty strings. It accepts the optional parameter "ariaLabel": if set, aria-label attribute is added to link
var value = parameters['field-id'].getHTMLStartEnd(ariaLabel); // Array of String

// Example of use
var linkObjectHTML = parameters['field-id'].getHTMLStartEnd(ariaLabel);
document.write(linkObjectHTML[0]);
document.write("<img src='...' />");
document.write(linkObjectHTML[1]);
```

## Margins
Allows to choose 4 margins. `DefaultValue` can contains up to 4 comma separated values, with the same meaning as CSS syntax:
- 1 value: all four sides
- 2 values: top and bottom | left and right
- 3 values: top | left and right | bottom
- 4 values: top | right | bottom | left

**Complete list of subtags**
```xml
<Field type="margins" id="">
  <DefaultValue>1</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].top; // integer
var value = parameters['field-id'].bottom; // integer
var value = parameters['field-id'].left; // integer
var value = parameters['field-id'].right; // integer
var leftMarginCSS = parameters['field-id'].leftMarginCSS; // CSS string like "margin-inline-start: 1px; "
var rightMarginCSS = parameters['field-id'].rightMarginCSS; // CSS string like "margin-inline-end: 1px; "
var leftPaddingCSS = parameters['field-id'].leftPaddingCSS; // CSS string like "padding-inline-start: 1px; "
var rightPaddingCSS = parameters['field-id'].rightPaddingCSS; // CSS string like "padding-inline-end: 1px; "
var marginCSS = parameters['field-id'].marginCSS; // CSS string like "margin-block: 1px 2px; margin-inline: 3px 4px; "
var paddingCSS = parameters['field-id'].paddingCSS; // CSS string like "padding-block: 1px 2px; padding-inline: 3px 4px; "
```

## MarginsHorVer
Available since v2024.1
Allows to choose 2 margins:
- `ShowHor == true` and `ShowVer == true`: horizontal and vertical
- `ShowHor == true` and `ShowVer == false`: left and right
- `ShowHor == false` and `ShowVer == true`: top and bottom
`DefaultValue` can contains 1 or 2 comma separated values, with the following meaning:
- 1 value: both sides
- 2 values: horizontal/left/top | vertical/right/bottom

**Complete list of subtags**
```xml
<Field type="marginshorver" id="field-id">
  <ShowHor>true</ShowHor>
  <ShowVer>true</ShowVer>
  <DefaultValue>5,3</DefaultHor>
  <MinValue>-10</MinValue>
  <MaxValue>10</MaxValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].hor; // integer (hor or left or top, depending on ShowHor and ShowVer configuration)
var value = parameters['field-id'].ver; // integer (ver or right or bottom, depending on ShowHor and ShowVer configuration)
```

## Number
Allows to choose a number

**Complete list of subtags**
```xml
<Field type="number" id="field-id">
  <DefaultValue>10</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <ShowDecimals>false</ShowDecimals>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].value; // Number
```

## Position
Available since v2024.1
Allows to choose the position of a element. The following combinations of `PositionType` and `ShowMiddleCenter` are supported; for each combination, `DefaultValue` XML tag in manifest and `position` JS property can assume different set of values, as reported in the following table:

| PositionType | ShowMiddleCenter | Allowed manifest XML tag values (JS property values are the same, but lowercase)                           |
|--------------|------------------|------------------------------------------------------------------------------------------------------------|
| All          | true             | TopLeft, TopCenter, TopRight, MiddleLeft, MiddleCenter, MiddleRight, BottomLeft, BottomCenter, BottomRight |
| Horizontal   | true             | Left, Center, Right                                                                                        |
| Horizontal   | false            | Left, Right                                                                                                |
| Vertical     | true             | Top, Middle, Bottom (available since v2024.2)                                                              |
| Vertical     | false            | Top, Bottom                                                                                                |
| Corner       | true             | TopLeft, TopRight, MiddleCenter, BottomLeft, BottomRight                                                   |
| Corner       | false            | TopLeft, TopRight, BottomLeft, BottomRight                                                                 |
| Side         | true             | Top, Bottom, Middle, Left, Right (available since v2024.2)                                                 |
| Side         | false            | Top, Bottom, Left, Right (available since v2024.2)                                                         |

**Complete list of subtags**
```xml
<Field type="position" id="pos">
  <PositionType>Horizontal</PositionType>
  <ShowMiddleCenter>true</ShowMiddleCenter>
  <DefaultValue>Left</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].positionType; // string (all, horizontal, vertical or corner)
var fieldValue = parameters['field-id'].showMiddleCenter; // bool
var fieldValue = parameters['field-id'].position; // string (see table above for possible values, depending on positionType and showMiddleCenter)
```

## RoundCorners
Allows to choose the rounding of the corners.

**Complete list of subtags**
```xml
<Field type="roundcorners" id="">
  <DefaultValue>1</DefaultValue>
  <MinValue>0</MinValue>
  <MaxValue>100</MaxValue>
  <Increment>5</Increment>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].topleft; // integer
var value = parameters['field-id'].topright; // integer
var value = parameters['field-id'].bottomleft; // integer
var value = parameters['field-id'].bottomright; // integer
var value = parameters['field-id'].topleftCSS; // CSS string like "border-start-start-radius: 1px; "
var value = parameters['field-id'].toprightCSS; // CSS string like "border-start-end-radius: 1px; "
var value = parameters['field-id'].bottomleftCSS; // CSS string like "border-end-start-radius: 1px; "
var value = parameters['field-id'].bottomrightCSS; // CSS string like "border-end-end-radius: 1px; "
var value = parameters['field-id'].CSS; // CSS string like "border-start-start-radius: 1px; border-start-end-radius: 2px; border-end-start-radius: 3px; border-end-end-radius: 4px; "
```

## Separator
Add a separator. It can change the behavior of a panel (column) inside the user interface.
It can have a `NewPanel` subtag which forces the creation of a new section in a new panel.

**Complete list of subtags**
```xml
<Field type="separator" id="">
  <Label l10n-id="loc_id">Default label text</Label>
  <NewPanel>true</NewPanel>
</Field>
```

## Shadow
Allows to choose the style of a shadow.

**Complete list of subtags**
```xml
<Field type="shadow" id="">
  <DefaultEnabled>false</DefaultEnabled>
  <DefaultColor>(#AARRGGBB|#RRGGBB)</DefaultColor>
  <DefaultOffsetX>1</DefaultOffsetX>
  <DefaultOffsetY>1</DefaultOffsetY>
  <DefaultDimension>10</DefaultDimension>
  <DefaultDiffusion>10</DefaultDiffusion>
  <ShowSpread>true</ShowSpread> <!-- Available since v2024.1 -->
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].active; // true if the 'enable' checkbox is checked
var value = parameters['field-id'].color (hexadecimal string);
var value = parameters['field-id'].colorR (integer 0-255);
var value = parameters['field-id'].colorG (integer 0-255);
var value = parameters['field-id'].colorB (integer 0-255);
var value = parameters['field-id'].colorA (integer 0-255);
var value = parameters['field-id'].offsetX (integer);
var value = parameters['field-id'].offsetY (integer);
var value = parameters['field-id'].blur (integer); // Dimension value
var value = parameters['field-id'].spread (integer); // Diffusion value
var value = parameters['field-id'].showSpread (bool); // Diffusion enabled (available since v2024.1)
```

## SiteNodes
Available since v2019.1.0.0
Allows to choose one o more site nodes from the site map.

**Complete list of subtags**
```xml
<Field type="sitenodes" id="">
  <EnableMultiSelection>false</EnableMultiSelection> <!-- If true the user can check more then one node [default: false] -->
  <DisablePages>false</DisablePages> <!-- If true the user is not able to select page nodes [default: false] -->
  <DisableLevels>false</DisableLevels> <!-- If true the user is not able to select level nodes [default: false] -->
  <DefaultValue>menu</DefaultValue> <!-- Possible values are: empty, root, menu, special, home [default: empty] -->
</Field>
```

**Not allowed configurations**
 - `DisablePages` && `DisableLevels`
 - `EnableMultiSelection` && `DisablePages`
 - `EnableMultiSelection` && `DisableLevels`
 - `DisableLevels` && `DefaultValue` is a Level
 - `DisablePages` && `DefaultValue` is a Page

**Complete example of WSX5 Script properties access**
```js
var idsArray = parameters['field-id'].nodes; // Array of selected nodes ids.
var node = wsx5.menu.getNode(idsArray[0]); // Use wsx5.menu to get sitenode infos
```

## StringList
Allows to add a list of strings.

**Complete list of subtags**
```xml
<Field type="stringlist" id="">
  <Label l10n-id="loc_id">Default label text</Label>
  <Height>278</Height>
  <Sorted>false</Sorted>
  <DefaultNewItem l10n-id="dni">New Item {0}</DefaultNewItem>
  <DefaultItem l10n-id="di1">Item 1</DefaultItem>
  <DefaultItem l10n-id="di2">Item 2</DefaultItem>
  <MinItems>0</MinItems>
  <MaxItems>2147483647</MaxItems>
  <Predefined>false</Predefined>
  <PredefinedItem>-1</PredefinedItem>
  <MultipleSelection>true</MultipleSelection>
  <LabelEdit>true</LabelEdit>
  <EditAfterAdd>true</EditAfterAdd>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].list; // Array of strings
var value = parameters['field-id'].keys; // Array of strings
var value = parameters['field-id'].predefined; // Integer
```

### Note about LabelEdit Field
Using a StringList with LabelEdit set to true can lead to deadlocks if the Selection Change event is registered and a Rich Text is present.

## Text
Show a text input.

**Complete list of subtags**
```xml
<Field type="text" id="field-id">
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

**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].value; // String
```

## Rich Text
Show a text editor.

**Complete list of subtags**
```xml
<Field type="richtext" id="field-id">
  <Label l10n-id="loc_id">Default label text</Label>
  <DefaultContent>DefaultContent</DefaultContent>
  <Height>393</Height>
  <Headings>false</Headings>
  <Font>false</Font>
  <BasicTextStyles>false</BasicTextStyles>
  <TextStyles>false</TextStyles>
  <TextAlignment>false</TextAlignment>
  <Lists>false</Lists>
  <Indentation>false</Indentation>
  <Image>false</Image>
  <ImageAlignment>false</ImageAlignment>
  <Tables>none</Tables>
  <RowsAndParagraphsStyles>false</RowsAndParagraphsStyles>
  <Separator>false</Separator>
  <AllLinks>false</AllLinks>
  <BasicLinks>false</BasicLinks>
  <DisableFileLinks>false</DisableFileLinks>
  <Tooltip>false</Tooltip>
  <HTML>false</HTML>
  <AutoWidth>false</AutoWidth>
  <Clipboard>none</Clipboard>
  <DarkBackground>false</DarkBackground>
  <UndoRedo>false</UndoRedo>
  <WidthAdapted>false</WidthAdapted>
  <SingleToolbar>false</SingleToolbar>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].HTML; // HTML string to be used into page
var fieldValue = parameters['field-id'].CSS; // CSS string to be used into style tag in header (GetHeaderContent Hook)
var fieldValue = parameters['field-id'].RawHTML; // String (Just copy as is to update the field later)
var fieldValue = parameters['field-id'].RawCSS; // String (Just copy as is to update the field later)
var fieldValue = parameters['field-id'].Links; // Array of String (Just copy as is to update the field later)
var fieldValue = parameters['field-id'].Headings; // Array of Object (Just copy as is to update the field later)
var fieldValue = parameters['field-id'].DarkBackground; // Boolean
var fieldValue = parameters['field-id'].AllowHTML; // Boolean
```

**Usage Example**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<App>
    <Name><![CDATA[Rich Text]]></Name>
    <Author><![CDATA[Incomedia]]></Author>
    <Version>1</Version>
    <Category>Miscellaneous</Category>
    <Groups>Utility</Groups>
    <Description l10n-id="description">Rich Text Example</Description>
    <Parameters>
        <Tab>
            <Label>Graphics</Label>
            <Fields>
                <Field type="richtext" id="rt">
                    <Clipboard>FullFeatured</Clipboard>
                    <UndoRedo>true</UndoRedo>
                    <BasicLinks>true</BasicLinks>
                    <AllLinks>true</AllLinks>
                    <DisableFileLinks>true</DisableFileLinks>
                    <Tooltip>true</Tooltip>
                    <Separator>true</Separator>
                    <Image>false</Image>
                    <HTML>true</HTML>
                    <AutoWidth>true</AutoWidth>
                    <DarkBackground>true</DarkBackground>
                    <Headings>true</Headings>
                    <Font>false</Font>
                    <TextStyles>true</TextStyles>
                    <TextAlignment>true</TextAlignment>
                    <Lists>true</Lists>
                    <Indentation>true</Indentation>
                    <RowsAndParagraphsStyles>true</RowsAndParagraphsStyles>
                    <ImageAlignment>true</ImageAlignment>
                </Field>
            </Fields>
        </Tab>
    </Parameters>
    <Output>
        <![CDATA[
            <div class="rich-text"><?wsx5 document.write(parameters.rt.HTML); ?></div>
        ]]>
    </Output>
    <Hooks>
       <![CDATA[
            function GetHeaderContents(type, currentContent) {
                if (type == 'css') {
                    var css = parameters.rt.CSS;
                    var finalCSS = "";
                    css.split("\n").forEach(function (line) {
                        line = line.trim();
                        if (line != '') {
                            if (line.indexOf('@') != 0 && line != '}') {
                                finalCSS += '#' + currentObject.id + ' .rich-text ' + line + '\n';
                            }
                            else {
                                finalCSS += line + '\n';
                            }
                        }
                    });
                    return '<style type="text/css">' + finalCSS + '</style>';
                }
                else {
                    return '';
                }
            }
       ]]>
    </Hooks>
</App>
```

## TextAlign
Available since v2024.1
Allows to choose text alignment.

**Complete list of subtags**
```xml
<Field type="textalign" id="field-id">
  <Align>left|center|right</Align>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].textAlign; // CSS string to be used into text-align property
var fieldValue = parameters['field-id'].textAlignCSS; // CSS string like "text-align: start; "
var fieldValue = parameters['field-id'].textAlignValue; // CSS string to be used into text-align property, RTL safe (returns start, center or end)
```
