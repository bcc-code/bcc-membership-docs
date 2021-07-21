# Webhooks
The Members System support webhooks. You can register your webhook in the UI or via the API. Currently we only support changes for the "person" entity.
## Menu
- [Home](index.md)
- [API integration](api-integration.md)
- [Webhooks integration](webhooks.md)
- [Data Structures and Scopes](data-structures-and-scopes.md)


## Webhook functionality (UI and API) -> Philip
_To access your application please see the [Getting Started](index.md) guid and the [Webhooks integration](webhooks.md) guide_
### Using the UI
![image](https://user-images.githubusercontent.com/12196246/126508777-0de66d0e-d1ab-49dd-971d-40c71776ccc0.png)
#### URL
The URL fields has to be a fully valid URL including the protocol(https), we don't add or remove anything when posting to this URL
#### Signing Key
The signing key is used to create a hash of the body of the request. This will gives you the ability to verify the origin of the HTTP POST  
#### Run Test
When implementing your webhook endpoint it might be nice to test it every now and then to make sure everything is on track. You can use the "Run Test" method for this. When you click this button we will take the currently logged in user and POST it to your webhook.
#### Request interval for data sync (ms)
When you click on "Sync Data" we will make sure to push all the persons your application have access to to your webhook. This might overload your system. The "Request interval for data sync" setting is there to prevent that, if you give this setting a value we will make sure not to POST request more frequent than what the value indicates. If the value is 0, we will POST message as fast as our system can scale to your endpoint.
 
 
 
 
  2. API - with code snippets
### How to configure webhook
  1. UI - with images
  2. API - with code snippets
### Signing Key
  1. UI - with images
  2. API - with code snippets
### Test webhook
  1. UI - with images
  2. API - with code snippets
//Read API part (api-integration.md) to structure this the same way

## Implementing webhooks in your app -> Mikolaj
1. confirming that webhook endpoint is properly exposed
1. how to decode a message (with code snippet)
2. body structure of a message
3. confirming validity/authenticity of a message
