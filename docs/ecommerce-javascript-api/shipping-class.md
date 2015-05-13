<a name="shipping"></a>
## shipping
x5engine.cart.shipping

**Kind**: global class  
**Summary**: Describe a shipping method. Usually you don&#x27;t want to directly instantiate this class but rather access to the instances created by WSX5 and stored in &#x60;x5engine.cart.manager&#x60;.
You may get them using &#x60;x5engine.cart.manager.shippings()&#x60;.  

* [shipping](#shipping)
  * [new shipping(settings)](#new_shipping_new)
  * [.base()](#shipping#base) ⇒ <code>Object</code>
  * [.id()](#shipping#id) ⇒ <code>String</code>
  * [.name()](#shipping#name) ⇒ <code>String</code>
  * [.description()](#shipping#description) ⇒ <code>String</code>
  * [.image()](#shipping#image) ⇒ <code>String</code>
  * [.price(includeVat, weight, amount)](#shipping#price) ⇒ <code>Number</code>
  * [.vat(weight, amount)](#shipping#vat) ⇒ <code>Number</code>
  * [.email()](#shipping#email) ⇒ <code>String</code>

<a name="new_shipping_new"></a>
### new shipping(settings)
Create a new Shipping object.


| Param | Type | Description |
| --- | --- | --- |
| settings | <code>Object</code> |  |
| settings.id | <code>String</code> | The shipping id |
| settings.name | <code>String</code> | The shipping name |
| settings.description | <code>String</code> | The shipping description |
| settings.precision | <code>Number</code> | The numbers precision |
| settings.vat | <code>Number</code> | The VAT as % |
| settings.type | <code>String</code> | The shipping type ("FIXED", "AMOUNT", "WEIGHT") |
| settings.price | <code>Number</code> | The shipping price (Can be a number or an object, basing on the shipping type) |
| settings.email | <code>String</code> | The shipping text to be shown in the customer's email |
| settings.image | <code>String</code> |  |

<a name="shipping#base"></a>
### .base() ⇒ <code>Object</code>
Provide the base settings for this class

**Kind**: instance method of <code>[shipping](#shipping)</code>  
<a name="shipping#id"></a>
### .id() ⇒ <code>String</code>
Provide the id of this shipping type

**Kind**: instance method of <code>[shipping](#shipping)</code>  
<a name="shipping#name"></a>
### .name() ⇒ <code>String</code>
Provide the name of this shipping type

**Kind**: instance method of <code>[shipping](#shipping)</code>  
<a name="shipping#description"></a>
### .description() ⇒ <code>String</code>
Provide the description of this shipping type

**Kind**: instance method of <code>[shipping](#shipping)</code>  
<a name="shipping#image"></a>
### .image() ⇒ <code>String</code>
Get the image url of this shipping type

**Kind**: instance method of <code>[shipping](#shipping)</code>  
<a name="shipping#price"></a>
### .price(includeVat, weight, amount) ⇒ <code>Number</code>
Return the price of this shipping

**Kind**: instance method of <code>[shipping](#shipping)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |
| weight | <code>Number</code> | The total weight of goods in the cart |
| amount | <code>Number</code> | The total amount of goods in the cart |

<a name="shipping#vat"></a>
### .vat(weight, amount) ⇒ <code>Number</code>
Return the vat of this shipping

**Kind**: instance method of <code>[shipping](#shipping)</code>  

| Param | Type | Description |
| --- | --- | --- |
| weight | <code>Number</code> | The total weight of goods in the cart |
| amount | <code>Number</code> | The total amount of goods in the cart |

<a name="shipping#email"></a>
### .email() ⇒ <code>String</code>
Return the email text of this shipping

**Kind**: instance method of <code>[shipping](#shipping)</code>  
