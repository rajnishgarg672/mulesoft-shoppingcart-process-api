# mulesoft-shoppingcart-process-api

+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [APIs security considerations](#apissecurityconsiderations)
+ [Run it!](#runit)
	* [Running on Studio](#runonstudio)
	* [Running on CloudHub](#runoncloudhub)
	* [Note](#RequiredDetailstorunonlocalandcloudhub)
	


# Use Case <a name="usecase"/>

As a Customer I want API to cover Shopping Cart functionality. 
The API provides endpoints for posting to the shopping cart, updating, deleting shopping cart and checkout. The details about product in shopping cart is fetch from the mulesoft-product-system-api.And checkout in mulesoft-shoppingcart-process-api is done by mulesoft-payment-gateway-sys-api.

### POST/shoppingCarts/
This endpoint will trigger flow createShoppingCart which creates shopping cart to Object Store for customer 


### PUT/shoppingCarts/{shoppingCartId}
This endpoint will trigger flow getShoppingCart which updates shopping cart from Object Store by shoppingCartId 

### DELETE/shoppingCarts/{shoppingCartId}
This endpoint will trigger flow deleteShoppingCart which removes shopping cart by shoppingCartId.

### POST/checkout/{shoppingCartId}
This endpoint will trigger flow checkout-implementation-logic which complete checkout experience by interacting with mulesoft-payment-gateway-sys-api for simulating dummy payment gateway.  

# Considerations <a name="considerations"/>

To run this api in local enviroment, there are certain preconditions that must be considered. **Failling to do so could lead to unexpected behavior of the api.**

## APIs security considerations <a name="apissecurityconsiderations"/>
This process API is  deployed to CloudHub and managed using the API Platform Manager.
   

# Run it! <a name="runit"/>
Simple steps to get Retail Shopping Cart Process API running.
See below.


### Where to Download Mule Studio and Mule ESB
Here are few tips to download Anypoint Studio.

+ You can download Mule Studio from this [Location](https://www.mulesoft.com/lp/dl/studio)


### Importing an mulesoft-shoppingcart-process-api into Studio
Anypoint Studio offers several ways to import a project into the workspace, for example: 

+ Anypoint Studio Project from File System
+ Packaged mule application (.jar)


### Running on Studio <a name="runonstudio"/>
Once you have imported  mulesoft-shoppingcart-process-api into Anypoint Studio you need to follow these steps to run it:

+ Locate the properties file `mulesoft-shoppingcart-process-api-<env>.properties`, in src/main/mule/resources we need to decrypt any credetials using masterKey
+ Once that is done, right click on you Anypoint mulesoft-shoppingcart-process-api project folder 
+ Hover you mouse over `"Run as"`
+ Click on  `"Mule Application(configure)"`.
+ Click on Enviromet tab.
+ click on Add.
+ Set new environment variable as "Name" : env and "Value" : sandbox
+ Set new environment variable as "Name" : masterKey and "Value" : *********************************


## Running on CloudHub <a name="runoncloudhub"/>
After deploying it to cloudhub, You need to go to `"Manage Application"` > `"Properties"` to set all environment variables detailed in **Properties to be configured**.

anypoint.platform.client_id=*********************************
anypoint.platform.base_url=https://anypoint.mulesoft.com/
anypoint.platform.analytics_base_url=https://analytics-ingest.anypoint.mulesoft.com
masterKey=*********************************
anypoint.platform.client_secret=*********************************
anypoint.platform.config.analytics.agent.enabled=false
env=sandbox

## Note <a name="RequiredDetailstorunonlocalandcloudhub"/>
Please refer Rajnish_ShoppingCart_project.pdf for details on masterKey as well as other credetails required to run in local as well as on cloudhub
