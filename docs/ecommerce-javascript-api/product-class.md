<a name="product"></a>
## product
x5engine.cart.product

**Kind**: global class  
**Summary**: Describe a product method. Usually you don&#x27;t want to directly instantiate this class but rather access to the instances created by WSX5 and stored in &#x60;x5engine.cart.manager&#x60;.
You may get them using &#x60;x5engine.cart.manager.store()&#x60;.  

* [product](#product)
  * [new product(productData, settings)](#new_product_new)
  * [.base()](#product#base) ⇒ <code>Object</code>
  * [.id()](#product#id) ⇒ <code>String</code>
  * [.quantity(n)](#product#quantity)
  * [.option(id)](#product#option) ⇒ <code>String</code>
  * [.subOption(id)](#product#subOption) ⇒ <code>String</code>
  * [.discount(includeVat)](#product#discount) ⇒ <code>Number</code>
  * [.singleFullPrice(includeVat)](#product#singleFullPrice) ⇒ <code>Number</code>
  * [.singlePrice(includeVat)](#product#singlePrice) ⇒ <code>Number</code>
  * [.fullPrice(includeVat)](#product#fullPrice) ⇒ <code>Number</code>
  * [.price(includeVat)](#product#price) ⇒ <code>Number</code>
  * [.singleVat(includeVat)](#product#singleVat) ⇒ <code>Number</code>
  * [.fullVat()](#product#fullVat) ⇒ <code>Number</code>
  * [.vat()](#product#vat) ⇒ <code>Number</code>
  * [.weight()](#product#weight) ⇒ <code>Number</code>
  * [.enableCoupon()](#product#enableCoupon) ⇒ <code>Boolean</code>
  * [.disableCoupon()](#product#disableCoupon) ⇒ <code>Boolean</code>

<a name="new_product_new"></a>
### new product(productData, settings)
Create a new Product object.


| Param | Type | Description |
| --- | --- | --- |
| productData | <code>Object</code> | The generic product data |
| settings | <code>Object</code> | The instance settings like option, suboption, quantity etc |
| settings.id | <code>String</code> | Software internal product id |
| settings.id_user | <code>String</code> | Product id set by the user |
| settings.category | <code>String</code> |  |
| settings.description | <code>String</code> |  |
| settings.price | <code>Number</code> |  |
| settings.images | <code>Array</code> |  |
| settings.link | <code>String</code> |  |
| settings.vat | <code>Number</code> |  |
| settings.vattype | <code>String</code> |  |
| settings.weight | <code>Number</code> |  |
| settings.avail | <code>String</code> |  |
| settings.precision | <code>Number</code> |  |
| settings.minQuantity | <code>Number</code> |  |

<a name="product#base"></a>
### .base() ⇒ <code>Object</code>
Provide the product settings

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#id"></a>
### .id() ⇒ <code>String</code>
Provide the product id

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#quantity"></a>
### .quantity(n)
Get or set the current quantity

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | The quantity |

<a name="product#option"></a>
### .option(id) ⇒ <code>String</code>
Get/Set the current option id

**Kind**: instance method of <code>[product](#product)</code>  
**Returns**: <code>String</code> - Option id  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>String</code> | Option id |

<a name="product#subOption"></a>
### .subOption(id) ⇒ <code>String</code>
Get/Set the current suboption id

**Kind**: instance method of <code>[product](#product)</code>  
**Returns**: <code>String</code> - SubOption id  

| Param | Type | Description |
| --- | --- | --- |
| id | <code>Number</code> | Suboption id |

<a name="product#discount"></a>
### .discount(includeVat) ⇒ <code>Number</code>
Provide the current discount

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |

<a name="product#singleFullPrice"></a>
### .singleFullPrice(includeVat) ⇒ <code>Number</code>
Get the single price without discount

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |

<a name="product#singlePrice"></a>
### .singlePrice(includeVat) ⇒ <code>Number</code>
Get the single element price

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |

<a name="product#fullPrice"></a>
### .fullPrice(includeVat) ⇒ <code>Number</code>
Get the current price without discount

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |

<a name="product#price"></a>
### .price(includeVat) ⇒ <code>Number</code>
Provide the current price with discount

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |

<a name="product#singleVat"></a>
### .singleVat(includeVat) ⇒ <code>Number</code>
Provide the vat for a single product

**Kind**: instance method of <code>[product](#product)</code>  

| Param | Type | Description |
| --- | --- | --- |
| includeVat | <code>Boolean</code> | True to include VAT |

<a name="product#fullVat"></a>
### .fullVat() ⇒ <code>Number</code>
Provide the VAT without discounts

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#vat"></a>
### .vat() ⇒ <code>Number</code>
Provide the VAT

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#weight"></a>
### .weight() ⇒ <code>Number</code>
Get the weight of this object

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#enableCoupon"></a>
### .enableCoupon() ⇒ <code>Boolean</code>
Activate the coupon discount

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#disableCoupon"></a>
### .disableCoupon() ⇒ <code>Boolean</code>
Disable the coupon activation

**Kind**: instance method of <code>[product](#product)</code>  
