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

**OnSelectionChanged()**
It is called when the user changes the selection of this stringlist field in the UI of WebSite X5. The output of this function will be used to [dynamically update fields values](dynamic-update-fields.md).

### Label Subtag
The **Label** subtag defines the label shown near the field. This tag can have:<br />- The `position` attribute with values "top", "left" or "none".<br />- The `width` attribute (since v11.0.8 to last v17) that must contain a number. The attribute is deprecated, however you can continue to use to configure the UI for versions <= v17.<br />- The `widthV2` attribute (since v2019.1) that is the new reference for the width (the `independentWidthAuto` must be false).<br />- The `independentWidthAuto` attribute (since v2019.1), if set to true the width will be calculated by the imInputControl control. The default is false.<br /><br />**Note**:<br />Since v2019.1 the label width will be calculated automatically from WSX5, section by section (from separator to separator): the width for each section will be the largest of the section's labels. (only those with positioning on the left). Labels with attributes `widthV2` and `independentWidthAuto` are not considered.



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
    <Options l10n-id="loc_id_1" value="value_1">default text 1</Options>
    <Options l10n-id="loc_id_2" value="value_2">default text 2</Options>
    <Options l10n-id="loc_id_3" value="value_3">default text 3</Options>
    <Options l10n-id="loc_id_4" value="value_4">default text 4</Options>
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
  <ShowOnlineLibrary>false</ShowOnlineLibrary> <!-- If set to true it allow using of PixaBay Images, false is the default: for fields that don't use images input don't use this tag -->
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
  <Label l10n-id="loc_id">Default label text</Label>
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
</Field>
```

**Complete example of WSX5 Script properties access**
```js
// "getHTML" method return text given wrapped by tag "a", if link was specified, otherwise only text given.
var value = parameters['field-id'].getHTML("link text html"); // String

// Example of use
if (parameters['field-id'].getHTML("#link#") != "#link#") { // link was specified
    document.write(parameters['field-id'].getHTML("link text html")); // <a href="[link value]">link text html</a>
} else {...} // link wasn't specified
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
var value = parameters['field-id'].topleft; // integer
var value = parameters['field-id'].topright; // integer
var value = parameters['field-id'].bottomleft; // integer
var value = parameters['field-id'].bottomright; // integer
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
  <DefaultNewItem l10n-id="dni">New Item</DefaultNewItem>
  <DefaultItem l10n-id="di1">Item 1</DefaultItem>
  <DefaultItem l10n-id="di2">Item 2</DefaultItem>
  <MinItems>0</MinItems>
  <Predefined>false</Predefined>
  <PredefinedItem>-1</PredefinedItem>
  <MultipleSelection>true</MultipleSelection>
</Field>
```

**Complete example of WSX5 Script properties access**
```js
var value = parameters['field-id'].list; // Array of strings
var value = parameters['field-id'].predefined; // Integer
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