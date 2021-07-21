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

## Implementing webhooks in your app -> Mikolaj
1. confirming that webhook endpoint is properly exposed
1. how to decode a message (with code snippet)
2. body structure of a message
3. confirming validity/authenticity of a message
