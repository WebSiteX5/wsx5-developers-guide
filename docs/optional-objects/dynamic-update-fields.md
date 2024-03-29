# Dynamically Update Fields Values and Storage

The [OnValueChanged](user-input-fields.md#hooks-subtag), [OnSelectionChanged](user-input-fields.md#hooks-subtag) and [OnMigration](hooks.md#onmigrationpreviousversion) hooks can return an output that will be used to dynamically update fields values.

The output may be an `Object` structured as follows:

|Property      |Type     |Description                                                                                                                                                                                                 |
|--------------|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|updatesPreview|`Boolean`|Overrides the default behavior of preview update for the changed field. **Note**: OnValueChanged and OnSelectionChanged only                                                                                |
|fields        |`Object` |Contains all the fields to be updated. Each field may be specified using its name as property. The structure of the value is based on the field type.                                                       |
|stringStorage |`Object` |Contains all the strings to be saved into storage. Object keys will be used as storage keys. Object values represent the strings themselves. An existing key can be removed by setting its value to `null`. |
|fieldToStorage|`Object` |Contains all the fields to be saved into storage. Object keys will be used as storage keys. Object values represent field ids. An existing key can be removed by setting its value to `null`.               |
|storageToField|`Object` |Contains all the fields to be recovered from storage. Object keys represent field ids. Object values represent storage keys.                                                                                |

`Object` properties will be processed in the order defined by this table. (i.e. if fieldToStorage and storageToField have the same key-field pair, only storage will change, field value will be recovered from storage as is)

Example:

```js
function OnValueChanged() {
    return {
        "updatesPreview": true,
        "fields": {
            "name": {
                "value": "John"
            }
        },
        "stringStorage": {
            "key": "value"
        },
        "fieldToStorage": {
            "key": "field-id"
        },
        "storageToField": {
            "field-id": "storage-key"
        }
    };
}
```

## Field Values Structures Examples

### BorderWidth

```js
{
    "left": 1, //integer
    "right": 2, //integer
    "top": 3, //integer
    "bottom": 4 //integer
}
```

### Checkbox

```js
{
    "checked": true //boolean
}
```

### Color

```js
{
    "valueR": 128, //integer
    "valueG": 128, //integer
    "valueB": 128, //integer
    "valueA": 128 //integer
}
```

### Colors

```js
{
    "topR": 128, //integer
    "topG": 128, //integer
    "topB": 128, //integer
    "topA": 128, //integer
    "bottomR": 32, //integer
    "bottomG": 64, //integer
    "bottomB": 128, //integer
    "bottomA": 256, //integer
    "leftR": 32, //integer
    "leftG": 32, //integer
    "leftB": 32, //integer
    "leftA": 256, //integer
    "rightR": 0, //integer
    "rightG": 0, //integer
    "rightB": 0, //integer
    "rightA": 0 //integer
}
```

### Dimension

```js
{
    "width": 100, //integer
    "widthUnit": "Fixed", //"Fixed" or "Percent"
    "height": 50 //integer
}
```

### Dropdown

```js
{
    "value": "Option 1" //string
}
```

### File

File fields cannot be updated using *value* key.

### FileList

FileList fields cannot be updated using *value* key.

### Font

```js
{
    "defaultFamily": true, //boolean
    "family": "Helvetica", //string
    "size": 10.5, //float
    "bold": true, //boolean
    "italic": false //boolean
}
```

### ImageSelect

ImageSelect fields cannot be updated using *value* key.

### Link

Link fields cannot be updated using *value* key.

### Margins

```js
{
    "top": 5, //integer
    "bottom": 5, //integer
    "left": 10, //integer
    "right": 10 //integer
}
```

### Number

```js
{
    "value": 12.5 //decimal
}
```

### RoundCorners

```js
{
    "topleft": 5, //integer
    "topright": 5, //integer
    "bottomleft": 5, //integer
    "bottomright": 5 //integer
}
```

### Separator

Separator has no values.

### Shadow

```js
{
    "active": true, //boolean
    "blur": 10, //integer
    "spread": 5, //integer
    "offsetX": 0, //integer
    "offsetY": 2, //integer
    "colorR": 32, //integer
    "colorG": 32, //integer
    "colorB": 32, //integer
    "colorA": 256 //integer
}
```

### SiteNodes

SiteNodes fields cannot be updated using *value* key.

### StringList

```js
{
    "list": [ //string array
        "hello",
        "world"
    ],
    "keys": [ //string array
        "lisfh5gi",
        "73w9b5e8"
    ],
    "predefined": 1 //integer
}
```

### Text

```js
{
    "value": "Hello world!" //string
}
```

### Rich Text

This field can be dynamically updated with these constraints only:
- Image parameter node be *false*
- DisableFileLinks node must be *true*
- Font node must be *false*

```js
{
    "RawHTML": "<b>Hello world!</b>", // string
    "RawCSS": "a { color: green; }", // string
    "Links": [ "<link data>", "<link data>" ], // string array
    "Headings": [ { "Id": 0, "Class": "", "Type": "H1" }, { "Id": 1, "Class": "", "Type": "H3" } ], // object array
    "DarkBackground": true, // boolean
    "AllowHTML": false // boolean
}
```