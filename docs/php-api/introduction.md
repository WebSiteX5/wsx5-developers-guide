# X5 Engine PHP API

WebSite X5 automatically loads the PHP Engine in its .php pages only if requested by a specific object inside the page.
For example, the PHP Engine is loaded if you place a Guestbook Object or a Dynamic Text Object inside the page.

If you want to use the PHP Engine in a .php page you created inside WebSite X5 and you are not sure if it's automatically loaded by the software, add the following code at the beginning of the page:
```php
<?php require_once('res/x5engine.php'); ?>
```