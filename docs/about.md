# Subscriptions

## Authentication

> API KeyHeaders

>|Security Scheme Type |API Key 
>|:--------------:|:--------: 
>|Header parameter name: |api_key

## Subscription

For data pushed to external apps when user Subscribes or Unsubscribes from service  

In both cases, your application will only need to return HTTP 200 Status for successful reception of the notification.

### Activation  

    {  
     "req_type": "MT_ACTIVATE",  
     "phone": "2547XXXXXXXX",  
     "product_id": "12345"   
    }

### Deactivation.

    {  
       "req_type": "MT_DEACTIVATE",  
        "phone": "2547XXXXXXXX",  
        "product_id": "12345"  
    }  

## sms
 
### Premium Messages  

For sending MO or MT Premium messages

    AUTHORIZATIONS:   APIKeyHeader  
    
    REQUEST BODY SCHEMA:   application/json

        product_id(required)    product_id(string) Used to identify the sms message sender         

