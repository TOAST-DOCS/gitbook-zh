## Contact Center > Online Contact > Service Guide (Consultation) > Customer Management

## Customer Info Contact
### Set Customer System API Information
![](http://static.toastoven.net/prod_contact_center/2.2.7-(1)_en.png)
When a call is received, the customer's **customer data** corresponding to the media number is **queried through the API** so that it can be displayed on the screen of the Online Contact. This function could be used after Customer Information Management function is activated in contract details.
This function could be used after **① enabling Open API**, and items to be input are as follows:

- **②** Send OC IP Information Email: If you select a user and press the Send email button, the IP address for opening the Online Contact Firewall will be sent via email.
- **③** API Route
- **④** API Method: Select between GET/POST.
- **⑤** Encrypt
- **⑥** Encrypt Type
- **⑦** Encrypt Key: New API Key would be created by clicking Change API Key.

API information would be saved through **Save** button, and the guide for the API can be checked in the following link. ([API Guide for Developers > Customer Data Connection](https://docs.nhncloud.com/en/Contact%20Center/en/online-contact-api-guide-openapi-customer-data/))

### Check Customer Information
![](http://static.toastoven.net/prod_contact_center/2.2.7-(2)_en.png)
When customer information API is enabled, **① Customer Management** tab will be displayed in the ticket which channel is **phone**. The customer information retrieved through the linked API is displayed in the appropriate tab, and when call is connected, current page is automatically moved to the **① Customer Management** tab to refer to the customer information during the call. 
