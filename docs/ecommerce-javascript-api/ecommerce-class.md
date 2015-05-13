<a name="ecommerce"></a>
## ecommerce
x5engine.cart.ecommerce

**Kind**: global class  
**Summary**: This class allows you to manage the entire JavaScript E-Commerce Cart of WebSite X5.
For example, you can add, remove or update the products in the cart, get the total amount of an order and save it to the database.

**Although the class has a contructor and can be instantiated by you, you may want to get the WSX5 global ecommerce instance stored in &#x60;x5engine.cart.manager&#x60;.**

If you need more info about the ecommerce data structure, you should take a look to the x5cart.js 
created by WebSite X5 and stored in the site&#x27;s &quot;cart&quot; folder.  

* [ecommerce](#ecommerce)
  * [new ecommerce(settings)](#new_ecommerce_new)
  * [.formatCurrency(n, format, currency)](#ecommerce#formatCurrency) ⇒ <code>String</code>
  * [.settings(newSetting)](#ecommerce#settings) ⇒ <code>Object</code>
  * [.form()](#ecommerce#form) ⇒ <code>Object</code>
  * [.add(productid, quantity, option, suboption, forceQuantity)](#ecommerce#add) ⇒ <code>String</code>
  * [.remove(hash)](#ecommerce#remove) ⇒ <code>Boolean</code>
  * [.update(hash, quantity, option, suboption)](#ecommerce#update) ⇒ <code>String</code>
  * [.cart()](#ecommerce#cart) ⇒ <code>Object</code>
  * [.count(boolean)](#ecommerce#count) ⇒ <code>Number</code>
  * [.category(categoryId)](#ecommerce#category) ⇒ <code>Object</code>
  * [.store(productId)](#ecommerce#store) ⇒ <code>Object</code>
  * [.shippings()](#ecommerce#shippings) ⇒ <code>Object</code>
  * [.shippingsCount()](#ecommerce#shippingsCount) ⇒ <code>Number</code>
  * [.payments()](#ecommerce#payments) ⇒ <code>Object</code>
  * [.paymentsCount()](#ecommerce#paymentsCount) ⇒ <code>Number</code>
  * [.payment(id, save)](#ecommerce#payment) ⇒ <code>Object</code>
  * [.shipping(id, save)](#ecommerce#shipping) ⇒ <code>Object</code>
  * [.userInvoiceData(data, save)](#ecommerce#userInvoiceData) ⇒ <code>Object</code>
  * [.userShippingData(data, save)](#ecommerce#userShippingData) ⇒ <code>Object</code>
  * [.vat()](#ecommerce#vat) ⇒ <code>Number</code>
  * [.fullPrice(includeVat)](#ecommerce#fullPrice) ⇒ <code>Number</code>
  * [.price(includeVat)](#ecommerce#price) ⇒ <code>Number</code>
  * [.paymentPrice(paymentid, includeVat, full)](#ecommerce#paymentPrice) ⇒ <code>Number</code>
  * [.paymentVat(paymentid, full)](#ecommerce#paymentVat) ⇒ <code>Number</code>
  * [.goodsFullPrice(includeVat)](#ecommerce#goodsFullPrice) ⇒ <code>Number</code>
  * [.goodsPrice(includeVat)](#ecommerce#goodsPrice) ⇒ <code>Number</code>
  * [.goodsWeight()](#ecommerce#goodsWeight) ⇒ <code>Number</code>
  * [.goodsVat()](#ecommerce#goodsVat) ⇒ <code>Number</code>
  * [.coupon(coupon, save, callback)](#ecommerce#coupon) ⇒ <code>Boolean</code>
  * [.canApplyCoupon()](#ecommerce#canApplyCoupon) ⇒ <code>Boolean</code>
  * [.canSetOrder()](#ecommerce#canSetOrder) ⇒ <code>Object</code>
  * [.isSetUserData()](#ecommerce#isSetUserData) ⇒ <code>Boolean</code>
  * [.paymentHTML(options)](#ecommerce#paymentHTML) ⇒ <code>String</code>
  * [.setOrder(callback)](#ecommerce#setOrder) ⇒ <code>void</code>
  * [.orderNumber()](#ecommerce#orderNumber) ⇒ <code>String</code>
  * [.empty(save)](#ecommerce#empty) ⇒ <code>void</code>
  * [.getStringifiedEncodedData()](#ecommerce#getStringifiedEncodedData) ⇒ <code>String</code>
  * [.getStringifiedFormData()](#ecommerce#getStringifiedFormData) ⇒ <code>String</code>
  * [.getStringifiedOrderData()](#ecommerce#getStringifiedOrderData) ⇒ <code>String</code>
  * [.bind(event, callback)](#ecommerce#bind) ⇒ <code>void</code>
  * [.unbind(event, callback)](#ecommerce#unbind) ⇒ <code>void</code>
  * [.restore(stringifiedEncodedData)](#ecommerce#restore) ⇒ <code>Boolean</code>
  * [.getLastOrderNumber()](#ecommerce#getLastOrderNumber) ⇒ <code>String</code>
  * [.clearLastOrderNumber()](#ecommerce#clearLastOrderNumber) ⇒

<a name="new_ecommerce_new"></a>
### new ecommerce(settings)
Instantiate a new E-Commerce manager passing half-a-ton of parameters.


| Param | Type | Description |
| --- | --- | --- |
| settings | <code>Object</code> |  |
| settings.indexpage | <code>String</code> | The cart page url relative to the site base url |
| settings.vat | <code>Number</code> | The default VAT |
| settings.coupon | <code>Boolean</code> | `true` to enable the coupons |
| settings.vattype | <code>String</code> | The type of VAT to use (none|included|excluded) |
| settings.currency | <code>String</code> | The currency symbol |
| settings.currency_id | <code>String</code> | The currency ID |
| settings.order_no_format | <code>String</code> | How to format the order number |
| settings.form_autocomplete | <code>Boolean</code> | Save form data in a cookie? |
| settings.form_validation | <code>String</code> | How to validate the user data forms |
| settings.showShipmentFields | <code>Boolean</code> | Must the cart show the shipment fields? |
| settings.continue_shopping_page | <code>String</code> | The default continue shopping page |
| settings.remove_from_cart_icon | <code>String</code> | Icon used to remove the goods from the cart |
| settings.add_to_cart_icon | <code>String</code> | Icon used to add the goods to the cart |
| settings.minimumAmount | <code>Number</code> | Minimum order amount (goods only) |
| settings.currencies | <code>Array</code> | Currencies available for automatic conversion (not enabled yet) |
| settings.cartCookie | <code>String</code> | The name of the cookie used to store the order data |
| settings.formCookie | <code>String</code> | The name of the cookie used to store the user's form data |
| settings.products | <code>Object</code> | // Array of products in stock (see the product class) |
| settings.shippings | <code>Object</code> | // Array of available shippings (see the shipping class) |
| settings.payments | <code>Object</code> | // Array of available payments (see the payment class) |

**Example**  
```js
var myEcommerce = new x5engine.cart.ecommerce({});
```
<a name="ecommerce#formatCurrency"></a>
### .formatCurrency(n, format, currency) ⇒ <code>String</code>
Format a number using the provided currency format.
The format parameter accepts the following chars:
- [C] to set the currency position
- @ to indicate a mandatory number in the decimal section
- \# to indicate a optional number in the decimal or integer section
- The first comma or period is used to divide 10^3 groups
- The second comma or period is used to divide decimal part from the integer part

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>String</code> - The formatted string  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | The number to format |
| format | <code>String</code> | The format to be applied |
| currency | <code>String</code> | String to use as currency |

**Example**  
```js
formatCurrency( 10.243, [C]#,###.@@, '€'); // Outputs €10.24
```
**Example**  
```js
formatCurrency( 1210.243, [C]#,###.@@, '€'); // Outputs €1,210.24
```
**Example**  
```js
formatCurrency( 1210.243, [C]#,###, '€'); // Outputs €1,210
```
<a name="ecommerce#settings"></a>
### .settings(newSetting) ⇒ <code>Object</code>
Provide the current cart settings

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| newSetting | <code>Object</code> | JSON with the new settings |

<a name="ecommerce#form"></a>
### .form() ⇒ <code>Object</code>
Provide the form fields set in the cart settings

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#add"></a>
### .add(productid, quantity, option, suboption, forceQuantity) ⇒ <code>String</code>
Add a product to the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>String</code> - The hash code useful to get/update/remove this product from the cart  

| Param | Type | Description |
| --- | --- | --- |
| productid | <code>String</code> | The product id |
| quantity | <code>Number</code> | The product quantity |
| option | <code>String</code> | The option id |
| suboption | <code>Number</code> | The suboption id |
| forceQuantity | <code>Boolean</code> | If true, the set quantity is not added to the current one but it replaces the actual |

<a name="ecommerce#remove"></a>
### .remove(hash) ⇒ <code>Boolean</code>
Remove an element from the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Boolean</code> - True if the element was removed correctly  

| Param | Type | Description |
| --- | --- | --- |
| hash | <code>String</code> | The hash id of the element in the cart |

<a name="ecommerce#update"></a>
### .update(hash, quantity, option, suboption) ⇒ <code>String</code>
Update the quantity for a gived product

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>String</code> - The new hash of the product, useful to get/update/remove this product from the cart  

| Param | Type | Description |
| --- | --- | --- |
| hash | <code>String</code> | The product hash |
| quantity | <code>Number</code> | The quantity |
| option | <code>String</code> | The option |
| suboption | <code>Number</code> | The suboption |

<a name="ecommerce#cart"></a>
### .cart() ⇒ <code>Object</code>
List the elements in the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#count"></a>
### .count(boolean) ⇒ <code>Number</code>
Return the number of goods in the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Description |
| --- | --- |
| boolean | deep True to keep quantity of each product in account |

<a name="ecommerce#category"></a>
### .category(categoryId) ⇒ <code>Object</code>
Return the products of a specified category.

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| categoryId | <code>String</code> | The category id |

<a name="ecommerce#store"></a>
### .store(productId) ⇒ <code>Object</code>
Provide the information about the products in the store or a single product in the store

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Object</code> - The product data  

| Param | Type | Description |
| --- | --- | --- |
| productId | <code>String</code> | The id of the searched product. Leave this empty to get the entire list of products. |

<a name="ecommerce#shippings"></a>
### .shippings() ⇒ <code>Object</code>
Provide a list of the available shippings

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#shippingsCount"></a>
### .shippingsCount() ⇒ <code>Number</code>
Provide the count of available shipping options

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#payments"></a>
### .payments() ⇒ <code>Object</code>
Provide a list of the available payments

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#paymentsCount"></a>
### .paymentsCount() ⇒ <code>Number</code>
Provide the count of available payment options

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#payment"></a>
### .payment(id, save) ⇒ <code>Object</code>
Get or set the payment method

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Object</code> - The current payment istance  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>String</code> | The payment id |
| save | <code>Boolean</code> | True to save the cart |

<a name="ecommerce#shipping"></a>
### .shipping(id, save) ⇒ <code>Object</code>
Set the shipping

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Object</code> - The current shipping istance  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>String</code> | The shipping id |
| save | <code>Boolean</code> | True to save the cart |

<a name="ecommerce#userInvoiceData"></a>
### .userInvoiceData(data, save) ⇒ <code>Object</code>
Set the user invoice data

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Object</code> - The invoice data  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>Object</code> | The invoice data |
| save | <code>Boolean</code> | True to save the cart |

<a name="ecommerce#userShippingData"></a>
### .userShippingData(data, save) ⇒ <code>Object</code>
Set the user shipping data

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Object</code> - The shipping data  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>Object</code> | The shipping data |
| save | <code>Boolean</code> | True to save the cart |

<a name="ecommerce#vat"></a>
### .vat() ⇒ <code>Number</code>
Provide the total VAT applied on the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#fullPrice"></a>
### .fullPrice(includeVat) ⇒ <code>Number</code>
Provide the total price of the order without discounts.

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include the VAT |

<a name="ecommerce#price"></a>
### .price(includeVat) ⇒ <code>Number</code>
Provide the total price of the order.

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include the VAT |

<a name="ecommerce#paymentPrice"></a>
### .paymentPrice(paymentid, includeVat, full) ⇒ <code>Number</code>
Get the payment price basing on the current cart contents

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| paymentid | <code>String</code> | The payment ID string |
| includeVat | <code>Boolean</code> | Include VAT or not? |
| full | <code>Boolean</code> | Full price or discounted |

<a name="ecommerce#paymentVat"></a>
### .paymentVat(paymentid, full) ⇒ <code>Number</code>
Get the payment VAT basing on the current cart contents

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| paymentid | <code>String</code> |  |
| full | <code>Boolean</code> | Full price or discounted |

<a name="ecommerce#goodsFullPrice"></a>
### .goodsFullPrice(includeVat) ⇒ <code>Number</code>
Provide the total amount of the goods in the cart without discounts

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include the VAT |

<a name="ecommerce#goodsPrice"></a>
### .goodsPrice(includeVat) ⇒ <code>Number</code>
Provide the total amount of the goods in the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include the VAT |

<a name="ecommerce#goodsWeight"></a>
### .goodsWeight() ⇒ <code>Number</code>
Provide the total weight of the goods in the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#goodsVat"></a>
### .goodsVat() ⇒ <code>Number</code>
Provide the total VAT applied on the products

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#coupon"></a>
### .coupon(coupon, save, callback) ⇒ <code>Boolean</code>
Apply a coupon code

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| coupon | <code>String</code> | The coupon code |
| save | <code>Boolean</code> | Set to true to save the cart after setting the value |
| callback | <code>function</code> | Execute this when the coupon is correctly loaded. It's called passing _coupon as parameter |

<a name="ecommerce#canApplyCoupon"></a>
### .canApplyCoupon() ⇒ <code>Boolean</code>
Return true if the user can apply a coupon on the current products in the cart or on the cart itself

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#canSetOrder"></a>
### .canSetOrder() ⇒ <code>Object</code>
Provide info about the actual cart status.

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>Object</code> - { 'success': true|false, 'message': '' }  
<a name="ecommerce#isSetUserData"></a>
### .isSetUserData() ⇒ <code>Boolean</code>
Return true in case the user data is correctly set

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#paymentHTML"></a>
### .paymentHTML(options) ⇒ <code>String</code>
Get the payment HTML code.

Each keyword is replaced using the following rules:

+ [PRICE]						= The price formatted using the default format
+ [PRICE, MULTIPLIER, FORMAT]	= The price formatted with a custom multiplier and format
+ [ORDER_NO]						= The order number
+ [ORDER_ENC_DATA]				= The order encrypted data, useful to restore the order itself
+ [UCASEKEYWORD]					= The original keyword taken from the user's invoice data
+ [SHIPPING_UCASEKEYWORD]		= The original keyword taken from the user's shipping data
+ [USE_SHIPPING_DATA]            = Is replaced by "true" or "false" boolean value if the user has compiled or not the shipping form

The available keywords on the INVOICE and SHIPPING sections are:
	[NAME], [LASTNAME], [ADDRESS1], [ADDRESS2], [CITY], [STATEREGION],
	[COUNTRY], [COUNTRYCODE] [ZIPPOSTALCODE], [EMAIL], [PHONE], [ADVERTS], [NOTE]
Moreover, any custom field is added using a custom ID so you can just use its ID in the keyword to replace it
in the HTML code.

##### HTML Escaping
Each keyword can be replaced with the HTML escaped version of its value by placing HESCAPE_ before it.

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>Object</code> | The options |

**Example**  
```js
[HESCAPE_PRICE] // Will be replaced with the HTML escaped price in the default format 

##### URL Escaping
Each keyword can be replaced with the URL escaped version of its value by placing UESCAPE_ before it.
```
**Example**  
```js
[UESCAPE_PRICE] // Will be replaced with the URL escaped price in the default format
```
<a name="ecommerce#setOrder"></a>
### .setOrder(callback) ⇒ <code>void</code>
Set the order

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>void</code> - The order number  

| Param | Type |
| --- | --- |
| callback | <code>function</code> | 

<a name="ecommerce#orderNumber"></a>
### .orderNumber() ⇒ <code>String</code>
Provide the order number

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#empty"></a>
### .empty(save) ⇒ <code>void</code>
Empty the cart

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| save | <code>Boolean</code> | True to save the cart |

<a name="ecommerce#getStringifiedEncodedData"></a>
### .getStringifiedEncodedData() ⇒ <code>String</code>
Encode the data of the cart, with order data and form data encoded to prevent privacy issues

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#getStringifiedFormData"></a>
### .getStringifiedFormData() ⇒ <code>String</code>
Stringify the saved form data

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#getStringifiedOrderData"></a>
### .getStringifiedOrderData() ⇒ <code>String</code>
Get a JSON string of the data to be saved

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
<a name="ecommerce#bind"></a>
### .bind(event, callback) ⇒ <code>void</code>
Bind a callback on a cart event

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type |
| --- | --- |
| event | <code>String</code> | 
| callback | <code>function</code> | 

<a name="ecommerce#unbind"></a>
### .unbind(event, callback) ⇒ <code>void</code>
Unbind a callback from a cart event

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type |
| --- | --- |
| event | <code>String</code> | 
| callback | <code>function</code> | 

<a name="ecommerce#restore"></a>
### .restore(stringifiedEncodedData) ⇒ <code>Boolean</code>
Restore the cart using the current data

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  

| Param | Type | Description |
| --- | --- | --- |
| stringifiedEncodedData | <code>String</code> | The encoded order string |

<a name="ecommerce#getLastOrderNumber"></a>
### .getLastOrderNumber() ⇒ <code>String</code>
Get the last order number

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: <code>String</code> - The last order made on the customer's PC or null  
<a name="ecommerce#clearLastOrderNumber"></a>
### .clearLastOrderNumber() ⇒
Clear the last order number

**Kind**: instance method of <code>[ecommerce](#ecommerce)</code>  
**Returns**: void  
