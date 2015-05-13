<a name="ImDb"></a>
## ImDb
**Kind**: global class  
**Summary**: A utility class which provides an easy access to the databases defined by the WSX5 user.
To use it, you must include __x5engine.php__ in your code.  

* [ImDb](#ImDb)
  * [new ImDb($host, $user, $pwd, $db)](#new_ImDb_new)
  * [.testConnection()](#ImDb#testConnection) ⇒ <code>Boolean</code>
  * [.closeConnection()](#ImDb#closeConnection) ⇒ <code>Void</code>
  * [.createTable($name, $fields)](#ImDb#createTable) ⇒ <code>Boolean</code>
  * [.deleteTable($table)](#ImDb#deleteTable) ⇒ <code>Void</code>
  * [.tableExists($table)](#ImDb#tableExists) ⇒ <code>Boolean</code>
  * [.error()](#ImDb#error) ⇒ <code>Array</code>
  * [.lastInsertId()](#ImDb#lastInsertId) ⇒ <code>Number</code>
  * [.query($query)](#ImDb#query) ⇒ <code>Array</code>
  * [.escapeString($string)](#ImDb#escapeString) ⇒ <code>String</code>
  * [.affectedRows()](#ImDb#affectedRows) ⇒ <code>Number</code>

<a name="new_ImDb_new"></a>
### new ImDb($host, $user, $pwd, $db)
Create a new ImDb Object


| Param | Type | Description |
| --- | --- | --- |
| $host | <code>String</code> | The database host address |
| $user | <code>String</code> | The database username |
| $pwd | <code>String</code> | The database password |
| $db | <code>String</code> | The database name |

<a name="ImDb#testConnection"></a>
### .testConnection() ⇒ <code>Boolean</code>
Check if the class is connected or not to a db

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>Boolean</code> - True if the class is connected to a DB. False otherwise.  
<a name="ImDb#closeConnection"></a>
### .closeConnection() ⇒ <code>Void</code>
Close the connection

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
<a name="ImDb#createTable"></a>
### .createTable($name, $fields) ⇒ <code>Boolean</code>
Create a new table or update an existing one.

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>Boolean</code> - True if the table was created succesfully.  

| Param | Type | Description |
| --- | --- | --- |
| $name | <code>String</code> | The table name |
| $fields | <code>Array</code> | The table fields list as array of associative arrays (one array item foreach table field). must be passed as stated in the example. |

**Example**  
```php
$db->createTable('tableName', array(
    "field1" => array(
        "type" => "INTEGER",
        "null" => false,
        "auto_increment" => true,
        "primary" => true
    ),
    "field2" => array(
        "type" => "TEXT",
        "null" => true,
        "auto_increment" => false,
        "more" => "CHARACTER SET UTF-8"
    ))
);
```
<a name="ImDb#deleteTable"></a>
### .deleteTable($table) ⇒ <code>Void</code>
Delete a table from the database.

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $table | <code>String</code> | The table name |

<a name="ImDb#tableExists"></a>
### .tableExists($table) ⇒ <code>Boolean</code>
Check if the table exists

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>Boolean</code> - True if the table exists. False otherwise.  

| Param | Type | Description |
| --- | --- | --- |
| $table | <code>String</code> | The table name |

<a name="ImDb#error"></a>
### .error() ⇒ <code>Array</code>
Get the last MySQL error.

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
<a name="ImDb#lastInsertId"></a>
### .lastInsertId() ⇒ <code>Number</code>
Provide the last inserted ID of the AUTOINCREMENT column

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>Number</code> - The id of the latest insert operation  
<a name="ImDb#query"></a>
### .query($query) ⇒ <code>Array</code>
Execute a MySQL query.

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>Array</code> - The query result or FALSE on error  

| Param | Type |
| --- | --- |
| $query | <code>String</code> | 

<a name="ImDb#escapeString"></a>
### .escapeString($string) ⇒ <code>String</code>
Escape a MySQL query string.

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>String</code> - The escaped string  

| Param | Type | Description |
| --- | --- | --- |
| $string | <code>String</code> | The string to escape |

<a name="ImDb#affectedRows"></a>
### .affectedRows() ⇒ <code>Number</code>
Return the number of affected rows in the last query.

**Kind**: instance method of <code>[ImDb](#ImDb)</code>  
**Returns**: <code>Number</code> - The number of affected rows.  
