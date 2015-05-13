<a name="payment"></a>
## payment
x5engine.cart.payment

**Kind**: global class  
**Summary**: Describe a payment method. Usually you don&#x27;t want to directly instantiate this class but rather access to the instances created by WSX5 and stored in &#x60;x5engine.cart.manager&#x60;.
You may get them using &#x60;x5engine.cart.manager.payments()&#x60;.  

* [payment](#payment)
  * [new payment(settings)](#new_payment_new)
  * [.base()](#payment#base) ⇒ <code>Object</code>
  * [.id()](#payment#id) ⇒ <code>String</code>
  * [.price(totalAmount, vattype)](#payment#price) ⇒ <code>Number</code>
  * [.vat(totalAmount)](#payment#vat) ⇒ <code>Number</code>
  * [.name()](#payment#name) ⇒ <code>String</code>
  * [.description()](#payment#description) ⇒ <code>String</code>
  * [.html()](#payment#html) ⇒ <code>String</code>
  * [.emailHtml()](#payment#emailHtml) ⇒ <code>String</code>
  * [.email()](#payment#email) ⇒ <code>String</code>
  * [.image()](#payment#image) ⇒ <code>String</code>

<a name="new_payment_new"></a>
### new payment(settings)
Instantiate a new Payment object.


| Param | Type | Description |
| --- | --- | --- |
| settings | <code>Object</code> | The payment settings |
| settings.id | <code>String</code> | The payment id |
| settings.name | <code>String</code> | The shipping name |
| settings.description | <code>String</code> | The shipping description |
| settings.image | <code>String</code> | The image url for this payment type |
| settings.email | <code>String</code> | The section to be sent in the email |
| settings.precision | <code>String</code> | The numbers precision |
| settings.vat | <code>String</code> | VAT as % |
| settings.vattype | <code>String</code> | VAT type ("none", "included", "excluded") |
| settings.pricetype | <code>String</code> | fixed|percentual how the price should be calculated? |
| settings.price | <code>String</code> | The price |
| settings.html | <code>String</code> | The payment HTML code |
| settings.emailHtml | <code>String</code> |  |

<a name="payment#base"></a>
### .base() ⇒ <code>Object</code>
Return the settings of this payment type

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#id"></a>
### .id() ⇒ <code>String</code>
Return the id of this payment type

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#price"></a>
### .price(totalAmount, vattype) ⇒ <code>Number</code>
Provide the price of this payment type

**Kind**: instance method of <code>[payment](#payment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| totalAmount | <code>Number</code> | The total amount in the cart |
| vattype | <code>String</code> | The type of vat (none|included|excluded) |

<a name="payment#vat"></a>
### .vat(totalAmount) ⇒ <code>Number</code>
Return the VAT of this payment type

**Kind**: instance method of <code>[payment](#payment)</code>  

| Param | Type | Description |
| --- | --- | --- |
| totalAmount | <code>Number</code> | The total amount in the cart |

<a name="payment#name"></a>
### .name() ⇒ <code>String</code>
Provide the name of this payment type

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#description"></a>
### .description() ⇒ <code>String</code>
Return the description

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#html"></a>
### .html() ⇒ <code>String</code>
Provide the HTML code to be shown to the user to complete the payment

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#emailHtml"></a>
### .emailHtml() ⇒ <code>String</code>
Provide the HTML code to be shown in an email message

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#email"></a>
### .email() ⇒ <code>String</code>
Provide the description to show in the email section of the payment

**Kind**: instance method of <code>[payment](#payment)</code>  
<a name="payment#image"></a>
### .image() ⇒ <code>String</code>
Provide the image url for this payment type

**Kind**: instance method of <code>[payment](#payment)</code>  
