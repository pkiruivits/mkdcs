# Welcome to Crossgate solutions SMS Gateway Documentation
# API Documentation
This API is a RESTful API. It uses standard RESTful error codes and custom message error codes.


## Request Headers:   
The details below will be needed for authentication.

>| Parameter | Data Type  |Description
>| --------- | :--------: | :------------:
>|app_key    |string      | Given on activating SMS service. Passed as a **header** value.
>|app_secret   |string      | Given on activating SMS service. Passed as a **header** value.


## 2. Request data:


### 2.1 Transactional SMS sending


Request Method: POST

Endpoint: /api/sendSms


Parameters needed:

>|Parameter |Datatype  |Required  |Description
>|-------- |:--------:  |:------: | :--------------
>|profile_id |Integer |Yes |Unique per sender profile. Given when send sms profile is activated.
>|phone_number |String |Yes |Recipient mobile number. Should start with 254 e.g 254712345678
>|message |String |Yes|The TEXT or SMS to send to recipient. Maximum allowed characters are 800.
>|reference_number |String |Optional|When given should be unique on every request as it checks and prevents duplicate sms from the clientapplication.
>|link_id |String |Optional|Required for MO based messages.
>|ttl |Integer |Optional |This field is reserved. When given, it validates the lifetime the sms should be valid for sending from the time the request is received. Given in seconds.


Sample send sms request JSON strucutre:

>{   
>>  "profile_id":123,   
>> "phone_number":"254700872844",   
>>"message":"Sample text SMS"  
>}

Sample send sms request JSON Response:

{  
"request_id": "53c426b8483e416b89450500ac1c5919",  
"sms_units_balance": 22,  
"message_length": 15,  
"sms_count": 1  
}

## 2.2.	Batch/Bulk SMS sending.

Request method :POST

Endpoint: /api/sendSmsBatch

Batch SMS parameters are a list of the transactional sms messages object parameters.

| Parameter |Datatype |Required |Description
|:--------: | :-------:| :------:|:--------
|profile_id |Integer |Yes| Unique per sender profile. Given when send sms profile is activated.
|batch_list |String | Yes |Check Transactional sms parameters. Passed as a list of objects. Current maximum batch_list size is 200 objects.

Sample Batch SMS sending:

{  

"profile_id":"1708151",  
"batch_list": [  

>>{   

>>>"message": "Dear Lorem ",  
>>>"phone_number": "254722912908", 

>>},  
>>{ 

>>>"message": "Dear Ipsum David ",  
>>>"phone_number": "254720151600",  
>>>"reference_number": "1234",  

>>}  
]  

}  

Sample Bacth sms body response:

>{  
>>"sms_units_balance": 22,  
>>"batch_list": [  
>>>{        
>>>"message_length": 15,  
>>>"message": "Dear Lorem ",  
>>>"request_id": "508d84f1c3da405e8c9d5eb406e14b01",  
>>>"phone_number": "254722912908",  
>>>"sms_count": 1  
>>>},  

>>>{  
>>>"message_length": 15,  
>>>"message": "Dear Ipsum David ",    
>>>"request_id": "5a572315c9994910bf4514c88f92b288",  
>>>"phone_number": "254720151600",  
>>>"reference_number": "1234",  
>>>"sms_count": 1 
>>>}  
>>],  
>"profile_id": "1708151"  

>}



## Commands
   To create a webpage using  this format you need to clearly understand how to travel using aeroplane
* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout
### Project layout
    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.
