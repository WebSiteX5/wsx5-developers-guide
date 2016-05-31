<a name="product"></a>

## product
x5engine.cart.product

**Kind**: global class  
**Summary**: Describe a product method. Usually you don&#x27;t want to directly instantiate this class but rather access to the instances created by WSX5 and stored in &#x60;x5engine.cart.manager&#x60;.
You may get them using &#x60;x5engine.cart.manager.store()&#x60;.  

* [product](#product)
  * [new product(productData, settings)](#new_product_new)
  * [.base()](#product#base) ⇒ <code>Object</code>
  * [.quiet(q)](#product#quiet) ⇒ <code>Boolean</code>
  * [.id()](#product#id) ⇒ <code>String</code>
  * [.quantity(n)](#product#quantity) ⇒ <code>Number</code>
  * [.availableOrThrow()](#product#availableOrThrow) ⇒ <code>Void</code>
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
| productData.id | <code>String</code> | Software internal product id |
| productData.id_user | <code>String</code> | Product id set by the user |
| productData.category | <code>String</code> | The Category ID |
| productData.description | <code>String</code> | The product description |
| productData.price | <code>Number</code> | The product price as a pure number |
| productData.images | <code>Array</code> | The images URLs array |
| productData.link | <code>String</code> | The link URL to place over the product image |
| productData.vat | <code>Number</code> | The VAT amount |
| productData.vattype | <code>String</code> | The VAT type. Default "none". |
| productData.weight | <code>Number</code> | The product's weight as a pure number |
| productData.availabilityType | <code>String</code> | The produt's availability type: "fixed" or "dynamic" |
| productData.staticAvailValue | <code>String</code> | The produt's static availability value. Default "unknown". |
| productData.precision | <code>Number</code> | The price's precision |
| productData.minQuantity | <code>Number</code> | The minimum quantity that should be ordered to make a valid order |
| productData.options | <code>Object</code> | The product's variations (options). This object contains the options ids as keys and the options data as values |
| productData.options.id.name | <code>String</code> | The variation name |
| productData.options.id.suboptions | <code>Array</code> | The array of strings with a list of the available sub options |
| productData.options.id.weightvar | <code>Number</code> | The weight variation for this option |
| productData.options.id.pricevar | <code>Number</code> | The price variation for this option |
| productData.discount | <code>Object</code> | The discount object |
| productData.discount.coupon | <code>String</code> | The discount coupon |
| productData.discount.type | <code>String</code> | The discount type: "relative" (percentual) or "absolute" |
| productData.discount.amount | <code>String</code> | The discount amount in percentual (0-1) if type is "relative" or as a pure number if type is "absolute" |
| productData.discount.coupon_start_date | <code>String</code> | The coupon's first day of validity |
| productData.discount.coupon_end_date | <code>String</code> | The coupon's last day of validity |
| productData.quantityDiscounts | <code>Object</code> | The product's quantity discounts. Each key is a quantity, each value the discount for the given minimum quantity |
| settings | <code>Object</code> | The instance settings like option, suboption, quantity etc |
| settings.quantity | <code>Object</code> | The number of products |
| settings.option | <code>Object</code> | The selected option id. Can be null. |
| settings.suboption | <code>Object</code> | The selected suboption id. Can be null. |

<a name="product#base"></a>
### .base() ⇒ <code>Object</code>
Provide the product settings

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#quiet"></a>
### .quiet(q) ⇒ <code>Boolean</code>
Enable or disable the quiet status for this product.

**Kind**: instance method of <code>[product](#product)</code>  
**Returns**: <code>Boolean</code> - The current value  
**Since**: 12.0.0  

| Param | Type | Description |
| --- | --- | --- |
| q | <code>Boolean</code> | If false, adding a quantity higher than the amount of stored items will throw an exception. |

<a name="product#id"></a>
### .id() ⇒ <code>String</code>
Provide the product id

**Kind**: instance method of <code>[product](#product)</code>  
<a name="product#quantity"></a>
### .quantity(n) ⇒ <code>Number</code>
Get or set the current quantity

**Kind**: instance method of <code>[product](#product)</code>  
**Returns**: <code>Number</code> - The current quantity  

| Param | Type | Description |
| --- | --- | --- |
| n | <code>Number</code> | The quantity |

<a name="product#availableOrThrow"></a>
### .availableOrThrow() ⇒ <code>Void</code>
Does nothing if the product is available or throw an error if the product is not available.
Available only in the Professional Edition.

**Kind**: instance method of <code>[product](#product)</code>  
**Since**: 12.0.0  
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
