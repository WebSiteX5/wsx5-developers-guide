<a name="imPrintJsError"></a>
## imPrintJsError($docType) ⇒ <code>Void</code>
Prints an error that warns the user that JavaScript is not enabled, then redirects to the previous page after 5 seconds.

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| $docType | <code>Boolean</code> | True to use the meta redirect with a complete document. False to use a javascript code. |

<a name="imPrintError"></a>
## imPrintError($message, $docType) ⇒ <code>Void</code>
Prints a custom error message then redirects to the previous page after 5 seconds.

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| $message | <code>String</code> | The message to show |
| $docType | <code>Boolean</code> | True to use the meta redirect with a complete document. False to use a javascript code. |

<a name="imCheckAccess"></a>
## imCheckAccess($page, $pathToRoot) ⇒ <code>Void</code>
Check if the current user can access to the provided page id.
If not, the user is redirected to the login page.

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| $page | <code>String</code> | The id of the page to check |
| $pathToRoot | <code>String</code> | The path to reach the root from the current folder |

<a name="showGuestBook"></a>
## showGuestBook($id, $filepath, $email, $captcha, $direct_approval) ⇒ <code>Void</code>
Show the guestbook
This function is provided as compatibility for v9 guestbook widget

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| $id | <code>String</code> | The guestbook id |
| $filepath | <code>String</code> | The folder where the comments must be stored |
| $email | <code>String</code> | The email to notify the new comments |
| $captcha | <code>Boolean</code> | true to show the captcha |
| $direct_approval | <code>Boolean</code> | true to directly approve comments |

<a name="getDbData"></a>
## getDbData($dbid) ⇒ <code>Array</code>
Provide the database connection data of given id

**Kind**: global function  
**Returns**: <code>Array</code> - an array like array('description' => '', 'host' => '', 'database' => '', 'user' => '', 'password' => '')  

| Param | Type | Description |
| --- | --- | --- |
| $dbid | <code>String</code> | The database id |

<a name="shuffleAssoc"></a>
## shuffleAssoc($list) ⇒ <code>Array</code>
Shuffle an associative array

**Kind**: global function  
**Returns**: <code>Array</code> - The shuffled array  

| Param | Type | Description |
| --- | --- | --- |
| $list | <code>Array</code> | The array to shuffle |

<a name="imstripos"></a>
## imstripos($haystack, $needle, $offset) ⇒ <code>Number</code>
If you want to support PHP 4 code, use this function instead of stripos.

**Kind**: global function  
**Returns**: <code>Number</code> - The position of the searched string  

| Param | Type | Description |
| --- | --- | --- |
| $haystack | <code>String</code> | Where to search |
| $needle | <code>String</code> | What to replace |
| $offset | <code>Number</code> | Start searching from here |

<a name="l10n"></a>
## l10n($id, $default) ⇒ <code>String</code>
Get a localization string.
The string is taken from the ones specified at step 1 of WSX5

**Kind**: global function  
**Returns**: <code>String</code> - The localization  

| Param | Type | Description |
| --- | --- | --- |
| $id | <code>String</code> | The localization key |
| $default | <code>String</code> | The default string |

<a name="pathCombine"></a>
## pathCombine($paths) ⇒ <code>String</code>
Combine a series of paths

**Kind**: global function  
**Returns**: <code>String</code> - The path created combining the elements of the array  

| Param | Type | Description |
| --- | --- | --- |
| $paths | <code>Array</code> | The array with the element of the path |

<a name="imstrtolower"></a>
## imstrtolower($str) ⇒ <code>String</code>
Try to convert a string to lowercase using multibyte encoding

**Kind**: global function  

| Param | Type |
| --- | --- |
| $str | <code>String</code> | 

<a name="checkJsAndSpam"></a>
## checkJsAndSpam($prt, $js) ⇒ <code>Bool</code>
Check for the valid data about spam and js

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| $prt | <code>String</code> | The spam post field name |
| $js | <code>String</code> | The js post file name |

<a name="in_array_field"></a>
## in_array_field($needle, $haystack, $all) ⇒ <code>Boolean</code>
Search if at least one element of $needle is in $haystack.

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| $needle | <code>Array</code> | Non-associative array |
| $haystack | <code>Array</code> | Non-associative array |
| $all | <code>Boolean</code> | Set to true to ensure that all the elements in $needle are in $haystack |

<a name="imFilterInput"></a>
## imFilterInput($var) ⇒ <code>Mixed</code>
Filter the var from unwanted input chars.
Basically remove the quotes added by magic_quotes

**Kind**: global function  
**Returns**: <code>Mixed</code> - The filtered var  

| Param | Type | Description |
| --- | --- | --- |
| $var | <code>Mixed</code> | The var to filter |

<a name="getLastAvailableDate"></a>
## getLastAvailableDate($timeArr) ⇒ <code>String</code>
Get the most recent date in the provided array of PHP times that do not define a future time.
The date is provided in the RSS format Sun, 15 Jun 2008 21:15:07 GMT

**Kind**: global function  

| Param | Type |
| --- | --- |
| $timeArr | <code>Array</code> | 

<a name="updateQueryStringVar"></a>
## updateQueryStringVar($name, $value) ⇒ <code>String</code>
Update the query string adding or updating a variable with a specified value

**Kind**: global function  
**Returns**: <code>String</code> - The updated query string  

| Param | Type | Description |
| --- | --- | --- |
| $name | <code>String</code> | The variable to be replaced |
| $value | <code>String</code> | The value to set |

<a name="addressFromEmail"></a>
## addressFromEmail($email) ⇒ <code>String</code>
Get the email address from a string formatted like "John Doe <johndoe@email.com>"

**Kind**: global function  
**Returns**: <code>String</code> - The email address  

| Param | Type | Description |
| --- | --- | --- |
| $email | <code>String</code> | The email string |

<a name="nameFromEmail"></a>
## nameFromEmail($email) ⇒ <code>String</code>
Get the user name from a string formatted like "John Doe <johndoe@email.com>"

**Kind**: global function  
**Returns**: <code>String</code> - The user name  

| Param | Type | Description |
| --- | --- | --- |
| $email | <code>String</code> | The email string |

<a name="imRequestHeaders"></a>
## imRequestHeaders() ⇒ <code>Array</code>
If you want to get the request headers and still support PHP 4, use this function.

**Kind**: global function  
**Returns**: <code>Array</code> - The request headers array or FALSE on failure  
