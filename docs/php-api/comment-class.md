<a name="ImComment"></a>
## ImComment
**Kind**: global class  
**Summary**: Manage the comment structure of a topic. It can load and save the comments from/to a file or a database.
To use it, you must include __x5engine.php__ in your code.

This class is available only in the **Professional**, **Evolution** and **Compact** editions.  

* [ImComment](#ImComment)
  * [new ImComment()](#new_ImComment_new)
  * [.loadFromXML($file)](#ImComment#loadFromXML) ⇒ <code>Void</code>
  * ~~[.loadFromOldFile($file)](#ImComment#loadFromOldFile) ⇒ <code>Void</code>~~
  * [.saveToXML($file)](#ImComment#saveToXML) ⇒ <code>Boolean</code>
  * [.saveToDb($host, $user, $password, $db, $table, $postid)](#ImComment#saveToDb) ⇒ <code>Boolean</code>
  * [.loadFromDb($host, $user, $password, $db, $table, $postid)](#ImComment#loadFromDb) ⇒ <code>Boolean</code>
  * [.add($comment)](#ImComment#add) ⇒ <code>Void</code>
  * [.sort($orderby, $sort)](#ImComment#sort) ⇒ <code>Void</code>
  * [.getAll($orderby, $sort, $approvedOnly)](#ImComment#getAll) ⇒ <code>Array</code>
  * [.getPage($pageNumber, $commentsPerPage, $orderby, $sort, $approvedOnly)](#ImComment#getPage) ⇒ <code>Array</code>
  * [.get($n)](#ImComment#get) ⇒ <code>Array</code>
  * [.getPagesNumber($commentsPerPage, $approvedOnly)](#ImComment#getPagesNumber) ⇒ <code>Number</code>
  * [.edit($n, $comment)](#ImComment#edit) ⇒ <code>Boolean</code>
  * [.delete($n)](#ImComment#delete) ⇒ <code>Void</code>
  * [.filterCode($str, $allow_links)](#ImComment#filterCode) ⇒ <code>String</code>
  * [.lastError()](#ImComment#lastError) ⇒ <code>Number</code>

<a name="new_ImComment_new"></a>
### new ImComment()
Build a new ImComment object.

<a name="ImComment#loadFromXML"></a>
### .loadFromXML($file) ⇒ <code>Void</code>
Load the comments from an xml file

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $file | <code>String</code> | The source file path |

<a name="ImComment#loadFromOldFile"></a>
### ~~.loadFromOldFile($file) ⇒ <code>Void</code>~~
***Deprecated***

Get the comments from a v8 comments file.
Use loadFromXML instead

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**See**: [loadFromXML](##imcommentloadfromxmlfile)  

| Param | Type | Description |
| --- | --- | --- |
| $file | <code>String</code> | The source file path |

<a name="ImComment#saveToXML"></a>
### .saveToXML($file) ⇒ <code>Boolean</code>
Save the comments in a xml file

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Boolean</code> - True if the file was saved correctly  

| Param | Type | Description |
| --- | --- | --- |
| $file | <code>String</code> | The destination file path |

<a name="ImComment#saveToDb"></a>
### .saveToDb($host, $user, $password, $db, $table, $postid) ⇒ <code>Boolean</code>
Save the comments in a DB.
**Available only in the Professional Edition**

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Boolean</code> - True if the comment was saved correctly  

| Param | Type | Description |
| --- | --- | --- |
| $host | <code>String</code> | The host name |
| $user | <code>String</code> | The user name |
| $password | <code>String</code> | The user password |
| $db | <code>String</code> | The db name |
| $table | <code>String</code> | The db table |
| $postid | <code>String</code> | The post id |

<a name="ImComment#loadFromDb"></a>
### .loadFromDb($host, $user, $password, $db, $table, $postid) ⇒ <code>Boolean</code>
Load the comments from a DB. This method is available only in the Professional edition.

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Boolean</code> - True if the data was loaded correctly. False instead.  

| Param | Type | Description |
| --- | --- | --- |
| $host | <code>String</code> | The host name |
| $user | <code>String</code> | The user name |
| $password | <code>String</code> | The user password |
| $db | <code>String</code> | The db name |
| $table | <code>String</code> | The db table |
| $postid | <code>String</code> | The post id |

<a name="ImComment#add"></a>
### .add($comment) ⇒ <code>Void</code>
Add a comment to a file

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $comment | <code>Array</code> | the array of data to store |

<a name="ImComment#sort"></a>
### .sort($orderby, $sort) ⇒ <code>Void</code>
Sort the array

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $orderby | <code>String</code> | Field to compare when ordering the array |
| $sort | <code>String</code> | Sort by ascending (asc) or descending (desc) order |

<a name="ImComment#getAll"></a>
### .getAll($orderby, $sort, $approvedOnly) ⇒ <code>Array</code>
Get all the comments loaded in this class

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Array</code> - An array of associative arrays containing the comments data  

| Param | Type | Description |
| --- | --- | --- |
| $orderby | <code>String</code> | Field to compare when ordering the array |
| $sort | <code>String</code> | Sort by ascending (asc) or descending (desc) order |
| $approvedOnly | <code>Boolean</code> | Show only approved comments |

<a name="ImComment#getPage"></a>
### .getPage($pageNumber, $commentsPerPage, $orderby, $sort, $approvedOnly) ⇒ <code>Array</code>
Get the comments in the specified page when there is the specified number of comments in every page.
This is useful for pagination.

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Array</code> - The list of comments in the page  

| Param | Type | Description |
| --- | --- | --- |
| $pageNumber | <code>Number</code> | The number of page to show (0 based) |
| $commentsPerPage | <code>Number</code> | Number of comments shown in each page |
| $orderby | <code>String</code> | Field to compare when ordering the array |
| $sort | <code>String</code> | Sort by ascending (asc) or descending (desc) order |
| $approvedOnly | <code>Boolean</code> | Show only approved comments |

<a name="ImComment#get"></a>
### .get($n) ⇒ <code>Array</code>
Get the comment number n

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Array</code> - The comment's data or an empty array if the comment is not found  

| Param | Type | Description |
| --- | --- | --- |
| $n | <code>Number</code> | The comment's number |

<a name="ImComment#getPagesNumber"></a>
### .getPagesNumber($commentsPerPage, $approvedOnly) ⇒ <code>Number</code>
Get the pages number given the number of comments per page

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Number</code> - The number of pages  

| Param | Type | Description |
| --- | --- | --- |
| $commentsPerPage | <code>Number</code> | Number of comments in every page |
| $approvedOnly | <code>Boolean</code> | Show only approved comments |

<a name="ImComment#edit"></a>
### .edit($n, $comment) ⇒ <code>Boolean</code>
Edit the comment number $n with the data contained in the parameter $comment

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
**Returns**: <code>Boolean</code> - True if the comment was correctly edited. False instead.  

| Param | Type | Description |
| --- | --- | --- |
| $n | <code>Number</code> | Comment number |
| $comment | <code>Array</code> | Comment data |

<a name="ImComment#delete"></a>
### .delete($n) ⇒ <code>Void</code>
Delete the comment at $n

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $n | <code>Number</code> | The index of the comment |

<a name="ImComment#filterCode"></a>
### .filterCode($str, $allow_links) ⇒ <code>String</code>
Clean the data from XSS

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $str | <code>String</code> | The string to parse |
| $allow_links | <code>Boolean</code> | true to allow links |

<a name="ImComment#lastError"></a>
### .lastError() ⇒ <code>Number</code>
Provide the last error

**Kind**: instance method of <code>[ImComment](#ImComment)</code>  
