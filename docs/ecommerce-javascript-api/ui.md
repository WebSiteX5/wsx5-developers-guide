<a name="module_x5engine.cart.ui"></a>
## x5engine.cart.ui
Contains the helpers used to interface some of the low level classes' methods with the user.
Basically it's a set of UI helpers.


* [x5engine.cart.ui](#module_x5engine.cart.ui)
  * [.addToCart(id, quantity, [option], [suboption], [skipToCart], [basePath])](#module_x5engine.cart.ui.addToCart) ⇒ <code>void</code>
  * [.resumeShopping()](#module_x5engine.cart.ui.resumeShopping) ⇒ <code>void</code>
  * [.updateWidget()](#module_x5engine.cart.ui.updateWidget) ⇒ <code>void</code>

<a name="module_x5engine.cart.ui.addToCart"></a>
### .addToCart(id, quantity, [option], [suboption], [skipToCart], [basePath]) ⇒ <code>void</code>
Add a new element to the cart managing the errors.
If an error occurs, the user in informed via an alert message.

**Kind**: static method of <code>[x5engine.cart.ui](#module_x5engine.cart.ui)</code>  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>Number</code> | The product id |
| quantity | <code>Number</code> | The quantity to add to the cart |
| [option] | <code>String</code> | The option id |
| [suboption] | <code>String</code> | The sub-option id |
| [skipToCart] | <code>Bool</code> | True to skip to cart summary page after adding the product |
| [basePath] | <code>String</code> | The basepath to the document root folder |

<a name="module_x5engine.cart.ui.resumeShopping"></a>
### .resumeShopping() ⇒ <code>void</code>
Return to the page from which the user got into the cart

**Kind**: static method of <code>[x5engine.cart.ui](#module_x5engine.cart.ui)</code>  
<a name="module_x5engine.cart.ui.updateWidget"></a>
### .updateWidget() ⇒ <code>void</code>
Called to update the cart widget

**Kind**: static method of <code>[x5engine.cart.ui](#module_x5engine.cart.ui)</code>  
