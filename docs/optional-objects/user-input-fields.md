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
| Indent         | no           | 0             | Indicates the indent level of the field according to the left border of the form. Must have a numerical integer value bigger or equal to zero.                                                      |
| Label          | no           | (empty)       | Defines the label shown near the field. This tag can have the `position` attribute with values "top", "left" or "none" and the `width` attribute (since v11.0.8) that must contain a number.        |
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
It is called when the user changes the value of this field in the UI of WebSite X5.

# Available field types

Here you can find a list of the available field types.
The values represented in the following XML code examples are not to consider as default values for the various fields.

## BorderWidth
Allows to choose the width of 4 borders.

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
  <DefaultValue>(#AARRGGBB|#RRGGBB)</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var fieldValue = parameters['field-id'].value; // CSS string like "#45ff23"
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
```

## Dimensions
Allows to choose width and height using a single UI control.

**Complete list of subtags**
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
```xml
<Field type="dropdown" id="" class="database">
  <Options>
    <Option l10n-id="localization_id" value="field_value">Default text</Option>
  </Options>
  <ShowNumbers>true</ShowNumbers>
  <DefaultValue>value_default_option</DefaultValue>
  <Label l10n-id="loc_id">Default label text</Label>
  <Hooks><![CDATA[
    function OnCreate() {
      // Must return the options array.
      // Each option element is defined via a JSON object
      // containing a text and a value property.
      return [{ text: "option text", value: "option value" }];
    }
    ]]>
  </Hooks>
</Field>
```
**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].value; // String
```

## File
Allows to choose a file.

**Complete list of subtags**
```xml
<Field type="file" id="">
  <Extensions>jpg,txt</Extensions>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].path; // String
var value = parameters['field-id'].name; // String
var value = parameters['field-id'].extension; // String
var value = parameters['field-id'].isImage; // Boolean
var value = parameters['field-id'].isUrl; // Boolean
var value = parameters['field-id'].width; // only if `isImage == true`
var value = parameters['field-id'].height; // only if `isImage == true`
var value = parameters['field-id'].clones; // only if `isImage == true`. Contains the list of clones of the image. Everyone has the fields shown above.
```

## FileList
Allows to choose a list of files.

**Complete list of subtags**
```xml
<Field type="filelist" id="">
  <Extensions>jpg,txt</Extensions>
  <AllowUrls>true</AllowUrls>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].list; // (array of FileSelect elements)
var value = parameters['field-id'].list.length; // (number of elements in the array)
var value = parameters['field-id'].list.path; // (path for the file example list[0].path prints the path of the first file)
```

## Font
It is a field which allows to choose the font, it's size and style.

**Complete list of subtags**
```xml
<Field type="font" id="">
  <DefaultFontFamily>Tahoma</DefaultFontFamily>
  <DefaultFontSize>10</DefaultFontSize>
  <DefaultBold>false</DefaultBold>
  <DefaultItalic>false</DefaultItalic>
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].family; // string
var value = parameters['field-id'].size; // integer pt
var value = parameters['field-id'].bold; // Boolean
var value = parameters['field-id'].italic; // Boolean
```

## Link
Allows to choose a link from the link selection window of WebSite X5.

**Complete list of subtags**
```xml
<Field type="link" id="">
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].getHTML("link text html"); // String
```

## Margins
Allows to choose 4 margins.

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
var value = parameters['field-id'].topLeft; // integer
var value = parameters['field-id'].topRight; // integer
var value = parameters['field-id'].bottomLeft; // integer
var value = parameters['field-id'].bottomRight; // integer
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
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].enabled;
var value = parameters['field-id'].color (hexadecimal string);
var value = parameters['field-id'].colorR (integer 0-255);
var value = parameters['field-id'].colorG (integer 0-255);
var value = parameters['field-id'].colorB (integer 0-255);
var value = parameters['field-id'].colorA (integer 0-255);
var value = parameters['field-id'].diffusion (integer);
var value = parameters['field-id'].dimension (integer);
```

## StringList
Allows to add a list of strings.

**Complete list of subtags**
```xml
<Field type="stringlist" id="">
  <Label l10n-id="loc_id">Default label text</Label>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].list; // Array of strings
```

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