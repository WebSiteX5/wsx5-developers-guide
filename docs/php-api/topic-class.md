<a name="ImTopic"></a>
## ImTopic
**Kind**: global class  
**Summary**: Manage the user messages in a topic or discussion.
To use it, you must include __x5engine.php__ in your code.  

* [ImTopic](#ImTopic)
  * [new ImTopic($id, $basepath, $postUrl)](#new_ImTopic_new)
  * [.setCommentsPerPage($n)](#ImTopic#setCommentsPerPage) ⇒ <code>Void</code>
  * [.setPostUrl($posturl)](#ImTopic#setPostUrl) ⇒ <code>Void</code>
  * [.setTitle($title)](#ImTopic#setTitle) ⇒ <code>Void</code>
  * [.loadXML($folder)](#ImTopic#loadXML) ⇒ <code>Void</code>
  * [.saveXML($folder)](#ImTopic#saveXML) ⇒ <code>Boolean</code>
  * [.loadDb($host, $user, $pwd, $db, $table)](#ImTopic#loadDb) ⇒ <code>Void</code>
  * [.saveDb($host, $user, $pwd, $db, $table)](#ImTopic#saveDb) ⇒ <code>Boolean</code>
  * [.showForm($rating, $captcha, $moderate, $email, $type, $moderateurl)](#ImTopic#showForm) ⇒ <code>Void</code>
  * [.showSummary($rating, $admin, $hideifempty)](#ImTopic#showSummary) ⇒ <code>Void</code>
  * [.showComments($page, $commentsPerPage, $rating, $order, $showabuse, $hideifempty)](#ImTopic#showComments) ⇒ <code>Void</code>
  * [.showPagination($page)](#ImTopic#showPagination) ⇒ <code>Void</code>
  * [.showRating()](#ImTopic#showRating) ⇒ <code>Void</code>

<a name="new_ImTopic_new"></a>
### new ImTopic($id, $basepath, $postUrl)
Create a new instance of ImTopic class


| Param | Type | Description |
| --- | --- | --- |
| $id | <code>String</code> | The topic id |
| $basepath | <code>String</code> | The base path |
| $postUrl | <code>String</code> | The URL to post to |

<a name="ImTopic#setCommentsPerPage"></a>
### .setCommentsPerPage($n) ⇒ <code>Void</code>
Set the number of comments to show in each page

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type |
| --- | --- |
| $n | <code>Number</code> | 

<a name="ImTopic#setPostUrl"></a>
### .setPostUrl($posturl) ⇒ <code>Void</code>
Set the path to wich the data is posted to when a message is submitted

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type |
| --- | --- |
| $posturl | <code>String</code> | 

<a name="ImTopic#setTitle"></a>
### .setTitle($title) ⇒ <code>Void</code>
Set the title of this topic

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type |
| --- | --- |
| $title | <code>String</code> | 

<a name="ImTopic#loadXML"></a>
### .loadXML($folder) ⇒ <code>Void</code>
Load the data from the xml file contained in the specified folder.
The filename of this topic is automatically calculated basing on the topic's id to provide a major lever of security.

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $folder | <code>String</code> | The file's folder |

<a name="ImTopic#saveXML"></a>
### .saveXML($folder) ⇒ <code>Boolean</code>
Save the data to an xml file in the provided folder.
The filename of this topic is automatically calculated basing on the topic's id to provide a major lever of security.

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  
**Returns**: <code>Boolean</code> - True if the file is saved correctly  

| Param | Type | Description |
| --- | --- | --- |
| $folder | <code>String</code> | The folder where is saved the file |

<a name="ImTopic#loadDb"></a>
### .loadDb($host, $user, $pwd, $db, $table) ⇒ <code>Void</code>
Load the data from the database.
This method is available only in the **Professional** edition.

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $host | <code>String</code> | The dbname |
| $user | <code>String</code> | The db user name |
| $pwd | <code>String</code> | The db user password |
| $db | <code>String</code> | The db name |
| $table | <code>String</code> | The db table |

<a name="ImTopic#saveDb"></a>
### .saveDb($host, $user, $pwd, $db, $table) ⇒ <code>Boolean</code>
Save the comments to a database.
This method is available only in the **Professional** edition.

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  
**Returns**: <code>Boolean</code> - True if the comments are saved correctly  

| Param | Type | Description |
| --- | --- | --- |
| $host | <code>String</code> | The dbname |
| $user | <code>String</code> | The db user name |
| $pwd | <code>String</code> | The db user password |
| $db | <code>String</code> | The db name |
| $table | <code>String</code> | The db table |

<a name="ImTopic#showForm"></a>
### .showForm($rating, $captcha, $moderate, $email, $type, $moderateurl) ⇒ <code>Void</code>
Show the comments form

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $rating | <code>Boolean</code> | true to show the rating |
| $captcha | <code>Boolean</code> | true to enable captcha |
| $moderate | <code>Boolean</code> | true to enable the moderation |
| $email | <code>String</code> | the email address to notificate |
| $type | <code>String</code> | guestbook or blog |
| $moderateurl | <code>String</code> | The url at wich is possible to moderate the new comments |

<a name="ImTopic#showSummary"></a>
### .showSummary($rating, $admin, $hideifempty) ⇒ <code>Void</code>
Show the topic summary

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $rating | <code>Boolean</code> | TRUE to show the ratings |
| $admin | <code>Boolean</code> | TRUE to show approved and unapproved comments |
| $hideifempty | <code>Boolean</code> | true to hide the summary if there are no comments |

<a name="ImTopic#showComments"></a>
### .showComments($page, $commentsPerPage, $rating, $order, $showabuse, $hideifempty) ⇒ <code>Void</code>
Show the comments list

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $page | <code>Number</code> | The page to show |
| $commentsPerPage | <code>Number</code> | The number of comments to show for each page |
| $rating | <code>Boolean</code> | True to show the ratings |
| $order | <code>String</code> | desc or asc |
| $showabuse | <code>Boolean</code> | True to show the "Abuse" button |
| $hideifempty | <code>Boolean</code> | True to hide the summary if there are no comments |

<a name="ImTopic#showPagination"></a>
### .showPagination($page) ⇒ <code>Void</code>
Show the pagination links for this topic

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  

| Param | Type | Description |
| --- | --- | --- |
| $page | <code>Number</code> | Page number |

<a name="ImTopic#showRating"></a>
### .showRating() ⇒ <code>Void</code>
Show a single rating form

**Kind**: instance method of <code>[ImTopic](#ImTopic)</code>  
