# Webhooks
The Members System support webhooks. You can register your webhook in the UI or via the API. Currently we only support changes for the "person" entity.
## Menu
- [Home](index.md)
- [API integration](api-integration.md)
- [Webhooks integration](webhooks.md)
- [Data Structures and Scopes](data-structures-and-scopes.md)


## Webhook functionality (UI and API)
To access your application please see the [Getting Started](index.md) guid and the [Webhooks integration](webhooks.md) guide.
## Using the UI
![image](https://user-images.githubusercontent.com/12196246/126508777-0de66d0e-d1ab-49dd-971d-40c71776ccc0.png)
###### URL
The URL fields has to be a fully valid URL including the protocol (https), we don't add or remove anything when posting to this URL
###### Signing Key
The signing key is used to create a hash of the body of the request. This will gives you the ability to verify the origin of the HTTP POST  
###### Run Test
When implementing your webhook endpoint it might be nice to test it every now and then to make sure everything is on track. You can use the "Run Test" method for this. When you click this button we will take the currently logged in user and POST it to your webhook.
###### Sync Data
When you click on "Sync Data" we will make sure to push all the persons your application have access to to your webhook. This might overload your system. The `Request interval for data sync` setting is there to prevent that, if you give this setting a value we will make sure not to POST requests more frequent than what the value indicates. If the value is 0, we will POST requests to your webhook as fast as our system can scale.
 
## Using the API
###### URL
Update `Webhook url` for application X. _(In order to remove the webhook set url to empty string)_
 ```js
 onst fetch = require('node-fetch');
    try {
        let updatedField = {
            webhook: {
                url: 'https://someurl.com/something'
            }
        }
        let httpResponse = await fetch('https://members.bcc.no/application/{APPLICATION-ID}',
            {
                method: 'patch',
                headers:
                    {   'Content-Type': 'application/json',
                        'x-access-token':'API-KEY-HERE'
                    },
                body: JSON.stringify(updatedField)
            })

        const result = await httpResponse.json()

        console.log('Updated the webhook url via API', result.webhook.url)
    } catch (error) {
        console.log(error.message)
    }
 ```
###### Signing Key
Update `Signing Key` for application X
 ```js
 const fetch = require('node-fetch');
    try {
        let updatedField = {
            webhook: {
                signingKey: 'helloWorld'
            }
        }
        let httpResponse = await fetch('https://members.bcc.no/application/{APPLICATION-ID}',
            {
                method: 'patch',
                headers:
                    {   'Content-Type': 'application/json',
                        'x-access-token':'API-KEY-HERE'
                    },
                body: JSON.stringify(updatedField)
            })

        const result = await httpResponse.json()
        
        console.log('Updated the signing key via API', result.webhook.url)
    } catch (error) {
        console.log(error.message)
    }
 ```
###### Run Test
Trigger a `webhook test` for application X
<br />
_Code snippet comming soon_
 
###### Sync Data
Trigger a `full sync` for application X
<br />
_Code snippet comming soon_

## Implementing webhooks in your app
To properly receive webhook messages in your application some preparation is needed.
Here you can find most important information on that topic.

### Confirming that webhook endpoint is properly exposed
For Members Webhooks to properly deliver messages, endpoint specified in Members UI/API must be a publicly accessible HTTPS address. The server for the push endpoint must have a valid SSL certificate signed by a certificate authority. If all these requirements are fullfilled endpoint should be able to receive requests.

### Receiving messages
When Members Webhooks delivers a message to a push endpoint, Members Webhooks sends the message in the body of a POST request. The body of the request is a JSON object and the message data is in the message.data field. The message data is base64-encoded.

Following is an example of message issued by Members Webhook:
```json
{
    "message": {
        "attributes": {
            "hash": "HashOfData"
        },
        "data": [{updatedPersonScopedData}],
        "messageId": "2070443601311540",
        "message_id": "2070443601311540",
        "publishTime": "2021-02-26T19:13:55.749Z",
        "publish_time": "2021-02-26T19:13:55.749Z",
    },
   "subscription": "idOfASubscription"
}
```
where ``` updatedPersonScopedData ``` is PersonDetails entity with removed properties according to scopes approved. PersonDetails schema can be found in [Data Structures and Scopes](data-structures-and-scopes.md)

### Confirming message
After you receive a push request, return an HTTP status code. To acknowledge the message, return one of the following status codes:
* 102
* 200
* 201
* 202
* 204

To send a negative acknowledgement for the message, return any other status code. If you send a negative acknowledgement or the acknowledgement deadline expires, Members Webhooks resends the message. You can't modify the acknowledgement deadline of individual messages that you receive from push subscriptions.

### Signing key

