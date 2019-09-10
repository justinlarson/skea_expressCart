
---
commit 399343a09d31977a75091a69ab4bbb527454a4b6

# Notes for you/your team

Behavior

* What does it do?
  * fully functional shopping cart 
* Who does it do this for? (internal / external customer base)
  * external
* What kind of information will it hold?
  * Product Information
  * Customer info
  * payment
  * PCI
* What are the different types of roles?
  * Admin
  * Customer
* What aspects concern your client/customer/staff the most?

Tech Stack

* Framework & Language: 
  * Nodejs 10, Handler Bars for templating
* 3rd party components, Examples:
  * Stripe, PayPal and Authorize.net 
* Datastore: Mongodb


Brainstorming / Risks
* Storing PCI
* Card Enumeration
* Email tampering
* Product Theft if business logic around checkout is bad (client-side: changing price)
* 3rd party account takeovers (Stripe, Paypal, Authorize.net)
* Nosql 
* Customer Data Loss 
* Webhooks
* XSS with using "{{{data}}}" 
* Authentication ( roll their own)
* Admin and Admin console access 
* API
* API key generation
* File upload 



Checklist of things to review based on Brainstorming and Tech Stack

- [ ] Look for instances of `{{{ }}}` in the template/views
- [ ] PCI data being stored
- [ ] Error being returned by invalid cards 
[Possibly returning verbose errors](https://github.com/mrvautin/expressCart/blob/399343a09d31977a75091a69ab4bbb527454a4b6/routes/payments/paypal.js#L63-L67) could be used to enumerate cards
- [ ] How are emails put together
- [ ] Cart and checkout procedures 
- [ ] check how the app integrates with third parties
- [ ] Check CRUD processes for injections
- [ ] Access control around user profiles
- [ ] Webhooks
- [ ] Authentication Flow 
- [ ] Look for template html escaping
- [ ] API access vs UI access
- [ ] Strong API key generation
- [ ] File upload process

Mapping / Routes

- [ ] routes/order.js:8:router.get('/admin/orders',
- [ ] routes/order.js:38:router.get('/admin/orders/bystatus/:orderstatus',
- [ ] routes/order.js:76:router.get('/admin/order/view/:id',
- [ ] routes/order.js:97:router.get('/admin/orders/filter/:search',
- [ ] routes/order.js:135:router.get('/admin/order/delete/:id',
- [ ] routes/order.js:155:router.post('/admin/order/statusupdate',
- [ ] routes/payments/paypal.js:7:router.get('/checkout_cancel',
- [ ] routes/payments/paypal.js:12:router.get('/checkout_return',
- [ ] routes/payments/paypal.js:109:router.post('/checkout_action',
- [ ] routes/payments/stripe.js:9:router.post('/checkout_action',
- [ ] routes/payments/authorizenet.js:9:router.post('/checkout_action',
- [ ] routes/user.js:8:router.get('/admin/users',
- [ ] routes/user.js:29:router.get('/admin/user/edit/:id',
- [ ] routes/user.js:58:router.get('/admin/user/new',
- [ ] routes/user.js:71:router.get('/admin/user/delete/:id',
- [ ] routes/user.js:90:router.post('/admin/user/update',
- [ ] routes/user.js:143:router.post('/admin/user/insert',
- [ ] routes/index.js:21:router.get('/payment/:orderId',
- [ ] routes/index.js:71:router.get('/checkout',
- [ ] routes/index.js:97:router.get('/pay',
- [ ] routes/index.js:124:router.get('/cartPartial',
- [ ] routes/index.js:138:router.get('/product/:id',
- [ ] routes/index.js:183:router.post('/product/updatecart',
- [ ] routes/index.js:247:router.post('/product/removefromcart',
- [ ] routes/index.js:276:router.post('/product/emptycart',
- [ ] routes/index.js:292:router.post('/product/addtocart',
- [ ] routes/index.js:414:router.get('/search/:searchTerm/:pageNum?',
- [ ] routes/index.js:468:router.get('/category/:cat/:pageNum?',
- [ ] routes/index.js:525:router.get('/sitemap.xml',
- [ ] routes/index.js:557:router.get('/page/:pageNum',
- [ ] routes/index.js:597:router.get('/:page?',
- [ ] routes/customer.js:10:router.post('/customer/create',
- [ ] routes/customer.js:63:router.get('/admin/customer/view/:id?',
- [ ] routes/customer.js:91:router.get('/admin/customers',
- [ ] routes/customer.js:114:router.get('/admin/customers/filter/:search',
- [ ] routes/customer.js:152:router.post('/customer/login_action',
- [ ] routes/customer.js:195:router.get('/customer/forgotten',
- [ ] routes/customer.js:209:router.post('/customer/forgotten_action',
- [ ] routes/customer.js:245:router.get('/customer/reset/:token',
- [ ] routes/customer.js:272:router.post('/customer/reset/:token',
- [ ] routes/customer.js:303:router.post('/customer/logout',
- [ ] routes/admin.js:16:router.get('/admin',
- [ ] routes/admin.js:21:router.get('/admin/logout',
- [ ] routes/admin.js:29:router.get('/admin/login',
- [ ] routes/admin.js:60:router.post('/admin/login_action',
- [ ] routes/admin.js:92:router.get('/admin/setup',
- [ ] routes/admin.js:119:router.post('/admin/setup_action',
- [ ] routes/admin.js:156:router.get('/admin/settings',
- [ ] routes/admin.js:172:router.post('/admin/createApiKey',
- [ ] routes/admin.js:193:router.post('/admin/settings/update',
- [ ] routes/admin.js:204:router.post('/admin/settings/option/remove',
- [ ] routes/admin.js:231:router.get('/admin/settings/menu',
- [ ] routes/admin.js:246:router.get('/admin/settings/pages',
- [ ] routes/admin.js:268:router.get('/admin/settings/pages/new',
- [ ] routes/admin.js:285:router.get('/admin/settings/pages/edit/:page',
- [ ] routes/admin.js:321:router.post('/admin/settings/pages/update',
- [ ] routes/admin.js:361:router.get('/admin/settings/pages/delete/:page',
- [ ] routes/admin.js:377:router.post('/admin/settings/menu/new',
- [ ] routes/admin.js:387:router.post('/admin/settings/menu/update',
- [ ] routes/admin.js:397:router.get('/admin/settings/menu/delete/:menuid',
- [ ] routes/admin.js:407:router.post('/admin/settings/menu/save_order',
- [ ] routes/admin.js:417:router.post('/admin/api/validate_permalink',
- [ ] routes/admin.js:443:router.post('/admin/file/upload',
- [ ] routes/admin.js:521:router.post('/admin/testEmail',
- [ ] routes/admin.js:529:router.post('/admin/file/delete',
- [ ] routes/admin.js:545:router.get('/admin/files',
- [ ] routes/product.js:12:router.get('/admin/products',
- [ ] routes/product.js:32:router.get('/admin/products/filter/:search',
- [ ] routes/product.js:62:router.get('/admin/product/new',
- [ ] routes/product.js:80:router.post('/admin/product/insert',
- [ ] routes/product.js:213:router.get('/admin/product/edit/:id',
- [ ] routes/product.js:244:router.post('/admin/product/update',
- [ ] routes/product.js:402:router.get('/admin/product/delete/:id',
- [ ] routes/product.js:429:router.post('/admin/product/published_state',
- [ ] routes/product.js:443:router.post('/admin/product/setasmainimage',
- [ ] routes/product.js:457:router.post('/admin/product/deleteimage',


## Mapping / Files

- [ ] /path/to/some/important/file.sh

