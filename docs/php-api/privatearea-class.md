<a name="imPrivateArea"></a>
## imPrivateArea
**Kind**: global class  
**Summary**: Provides a set of useful methods for managing the private area, the users and the accesses.
To use it, you must include __x5engine.php__ in your code.  

* [imPrivateArea](#imPrivateArea)
  * [new imPrivateArea()](#new_imPrivateArea_new)
  * [.getInstance()](#imPrivateArea#getInstance) ⇒ <code>Imprivatearea</code>
  * [.login($uname, $pwd)](#imPrivateArea#login) ⇒ <code>Number</code>
  * [.logout()](#imPrivateArea#logout) ⇒ <code>Void</code>
  * [.savePage()](#imPrivateArea#savePage) ⇒ <code>Void</code>
  * ~~[.who_is_logged()](#imPrivateArea#who_is_logged) ⇒ <code>Mixed</code>~~
  * [.whoIsLogged()](#imPrivateArea#whoIsLogged) ⇒ <code>Mixed</code>
  * [.checkAccess($page)](#imPrivateArea#checkAccess) ⇒ <code>Number</code>
  * [.getLandingPage()](#imPrivateArea#getLandingPage) ⇒ <code>Mixed</code>
  * [.messageFromStatusCode($code)](#imPrivateArea#messageFromStatusCode) ⇒ <code>String</code>
  * [.getUserByUsername($id)](#imPrivateArea#getUserByUsername) ⇒ <code>Mixed</code>
  * [.getUsersById($ids)](#imPrivateArea#getUsersById) ⇒ <code>Array</code>
  * [.setDBData($host, $username, $password, $dbname, $dbtable)](#imPrivateArea#setDBData) ⇒ <code>Void</code>
  * [.validateWaitingUserById($dbid)](#imPrivateArea#validateWaitingUserById) ⇒ <code>Bool</code>
  * [.validateWaitingUserByKey($keys, $login)](#imPrivateArea#validateWaitingUserByKey) ⇒ <code>Booleal</code>
  * [.removeWaitingUsers($ts, $usersToKeep)](#imPrivateArea#removeWaitingUsers) ⇒ <code>Void</code>
  * [.getKeyFromId($dbid)](#imPrivateArea#getKeyFromId) ⇒ <code>String</code>
  * [.createUsersTable()](#imPrivateArea#createUsersTable) ⇒ <code>Void</code>
  * [.registerNewUser($username, $password, $email, $validated)](#imPrivateArea#registerNewUser) ⇒ <code>Number</code>
  * [.sendNotificationEmail($id)](#imPrivateArea#sendNotificationEmail) ⇒ <code>Void</code>
  * [.sendValidationEmail($id)](#imPrivateArea#sendValidationEmail) ⇒ <code>Void</code>
  * [.sendLostPasswordEmail($data)](#imPrivateArea#sendLostPasswordEmail) ⇒ <code>Boolean</code>

<a name="new_imPrivateArea_new"></a>
### new imPrivateArea()
Create a new ImDb Object

<a name="imPrivateArea#getInstance"></a>
### .getInstance() ⇒ <code>Imprivatearea</code>
Get the instance of the private area

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Imprivatearea</code> - The instance of a private area  
<a name="imPrivateArea#login"></a>
### .login($uname, $pwd) ⇒ <code>Number</code>
Login a user with username and password

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Number</code> - An error code:
                 -5 if the user email is not validated,
                 -2 if the username or password are invalid,
                 -1 if there's a db error,
                 0 if the process exits correctly  

| Param | Type | Description |
| --- | --- | --- |
| $uname | <code>String</code> | Username |
| $pwd | <code>String</code> | Password |

<a name="imPrivateArea#logout"></a>
### .logout() ⇒ <code>Void</code>
Logout a user

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
<a name="imPrivateArea#savePage"></a>
### .savePage() ⇒ <code>Void</code>
Save the current page as the referer

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
<a name="imPrivateArea#who_is_logged"></a>
### ~~.who_is_logged() ⇒ <code>Mixed</code>~~
***Deprecated***

Use whoIsLogged instead

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
<a name="imPrivateArea#whoIsLogged"></a>
### .whoIsLogged() ⇒ <code>Mixed</code>
Get an array of data about the logged user

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Mixed</code> - An array containing the data of the current logged user or false if no user is logged.  
<a name="imPrivateArea#checkAccess"></a>
### .checkAccess($page) ⇒ <code>Number</code>
Check if the logged user can access to a specific page.
The page is provided using its page id.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Number</code> - 0 if the current user can access the page, 
                -2 if the XSS security checks are not met
                -3 if the user is not logged
                -4 if the user is still not validated
                -8 if the user cannot access the page  

| Param | Type | Description |
| --- | --- | --- |
| $page | <code>Number</code> | The page id. You can retrieve the page id from the file x5settings.php. |

<a name="imPrivateArea#getLandingPage"></a>
### .getLandingPage() ⇒ <code>Mixed</code>
Get the current user's landing page.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Mixed</code> - The filename of the user's landing page or false if the user is not logged.  
<a name="imPrivateArea#messageFromStatusCode"></a>
### .messageFromStatusCode($code) ⇒ <code>String</code>
Convert a status code to a text message

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>String</code> - The text message related to the provided error code  

| Param | Type | Description |
| --- | --- | --- |
| $code | <code>Number</code> | The error code |

<a name="imPrivateArea#getUserByUsername"></a>
### .getUserByUsername($id) ⇒ <code>Mixed</code>
Get the data about a user.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Mixed</code> - The user's data (As associative array) or null if the user is not found.
The associative array contains the following keys: id, ts, ip, username, password, realname, email, key, validated, groups  

| Param | Type | Description |
| --- | --- | --- |
| $id | <code>String</code> | The username |

<a name="imPrivateArea#getUsersById"></a>
### .getUsersById($ids) ⇒ <code>Array</code>
Get the user data relative to a set of user ids.
This method is available only in the **Professional** edition.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Array</code> - An array of associative arrays containing the users' data.
The array keys are: id, ts, ip, username, password, realname, email, key, validated  

| Param | Type | Description |
| --- | --- | --- |
| $ids | <code>Array</code> | The array of user ids. |

<a name="imPrivateArea#setDBData"></a>
### .setDBData($host, $username, $password, $dbname, $dbtable) ⇒ <code>Void</code>
Setup the db connection.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  

| Param | Type |
| --- | --- |
| $host | <code>String</code> | 
| $username | <code>String</code> | 
| $password | <code>String</code> | 
| $dbname | <code>String</code> | 
| $dbtable | <code>String</code> | 

<a name="imPrivateArea#validateWaitingUserById"></a>
### .validateWaitingUserById($dbid) ⇒ <code>Bool</code>
Validate the waiting users listed in $ids. It must be an array of DB ids.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  

| Param | Type |
| --- | --- |
| $dbid | <code>Array</code> | 

<a name="imPrivateArea#validateWaitingUserByKey"></a>
### .validateWaitingUserByKey($keys, $login) ⇒ <code>Booleal</code>
Validate the waiting users listed in $keys. It must be an array of DB keys.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $keys | <code>Array</code> |  |
| $login | <code>Boolean</code> | Automatically login the user if validation is succesful |

<a name="imPrivateArea#removeWaitingUsers"></a>
### .removeWaitingUsers($ts, $usersToKeep) ⇒ <code>Void</code>
Remove the remaining waiting users.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $ts | <code>String</code> | Remove only the users registered before this timestamp. |
| $usersToKeep | <code>Array</code> | Remove all the users but keep the ones listed in this array |

<a name="imPrivateArea#getKeyFromId"></a>
### .getKeyFromId($dbid) ⇒ <code>String</code>
Get the validation key of user $dbid.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>String</code> - The validation key  

| Param | Type |
| --- | --- |
| $dbid | <code>String</code> | 

<a name="imPrivateArea#createUsersTable"></a>
### .createUsersTable() ⇒ <code>Void</code>
Create the users table if it doesn't exist
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
<a name="imPrivateArea#registerNewUser"></a>
### .registerNewUser($username, $password, $email, $validated) ⇒ <code>Number</code>
Register a new user in the database.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Number</code> - the user's ID or the error number (-1: user already exists, -2: generic error)  

| Param | Type |
| --- | --- |
| $username | <code>String</code> | 
| $password | <code>String</code> | 
| $email | <code>String</code> | 
| $validated | <code>String</code> | 

<a name="imPrivateArea#sendNotificationEmail"></a>
### .sendNotificationEmail($id) ⇒ <code>Void</code>
Notify the registration of a new user to the site's owner.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $id | <code>Number</code> | The user id |

<a name="imPrivateArea#sendValidationEmail"></a>
### .sendValidationEmail($id) ⇒ <code>Void</code>
Send the validation email for the user indentified by $id.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  

| Param | Type |
| --- | --- |
| $id | <code>String</code> | 

<a name="imPrivateArea#sendLostPasswordEmail"></a>
### .sendLostPasswordEmail($data) ⇒ <code>Boolean</code>
If the user has provided an email address, he receives a message with his password.
If the user's email is not available, the request is notified to the site's admin.
This method is only available in the **Professional edition**.

**Kind**: instance method of <code>[imPrivateArea](#imPrivateArea)</code>  
**Returns**: <code>Boolean</code> - True if the email is sent correctly.  

| Param | Type | Description |
| --- | --- | --- |
| $data | <code>String</code> | The user's email or username |

<a name="getSavedPage"></a>
## getSavedPage() ⇒ <code>Mixed</code>
Return the referer page name (the one which caused the user to land on the login page).

**Kind**: global function  
**Returns**: <code>Mixed</code> - The name of the page or false if no referer is available.  
