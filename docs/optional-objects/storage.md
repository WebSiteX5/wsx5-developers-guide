# Storage
**Since**: 2021.5.5

Storage is a key-value dictionary that the developer can use to save 2 kinds of data: strings and field values.

The data saved into Storage can be used to manage [dynamic fields](dynamic-update-fields.md) and generate the Optional Object output.

The saved data will be stored inside the Project and will be always accessible thru WSX5Script.

This feature has the primary objective to let the developer save full Field data into Storage, including files and fonts.

## Reading the Storage
Storage can be read in any WSX5Script thru the [storage object](wsx5-script.md#storage).

## Writing into Storage and Fields
Storage can be written by following the procedure described for [dynamic update](dynamic-update-fields.md).

The same procedure describes how to update fields with the data previously saved into storage.
