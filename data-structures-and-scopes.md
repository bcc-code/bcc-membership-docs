# Data Structures and Scopes
This section describe `person` object and how it relates to scopes.

## Menu
- [Home](index.md)
- [API integration](api-integration.md)
- [Webhooks integration](webhooks.md)
- [Data Structures and Scopes](data-structures-and-scopes.md)

## Scopes
Currently Members supports the following scopes
#### Identity (These scopes are consistent with OIDC scopes related to claims)
- `email`
- `phone`
- `profile`
- `address`


#### Members (Custom Scopes)
- `members.read_membership`
- `members.read_family`

Once you have the "Technical Administrator" role ([See Getting Started](index.md)) you will be able to log in to members and apply for these scopes for your application. See [API integration](api-integration.md) it shows the navigation to your application.

## Data Structure
Currently these scopes are all related to the `person` object and looks maps to the scopes as follows

###### `default` (You automatically get provided with the "personID" even if you have not scopes approved)
```json
  {
    "personID": 54512
  }
```
###### `email`
```json
  {
    "personID": 54512,
    "email": "philly.daly@gmail.com"
  }
```
###### `phone`
```json
  {
    "personID": 54512,
    "cellPhone": {
      "formatted": "+47 925 07 748",
      "number": " 925 07 748",
      "prefix": "47",
      "unFormatted": "+4792507748"
    },
    "homePhone": {
      "formatted": "+47 925 07 748",
      "number": " 925 07 748",
      "prefix": "47",
      "unFormatted": "+4792507748"
    }
  }
```
###### `profile`
```json
  {
    "personID": 54512,
    "firstName": "Philly",
    "middleName": "Pelle",
    "lastName": "Daly",
    "displayName": "Philly Pelle Daly",
    "birthDate": "1988-12-08T00:00:00",
    "genderCode": 1,
    "cultureCode1": "en-US",
    "profilePicture": "https://storage.googleapis.com/kinetic-center-276213_profile-pictures/178509735_a0mdd0q2qh.jpg",
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `address`
```json
 {
    "personID": 54512,
    "currentAddress": {
      "address1": "testAddress3",
      "city": "Ås",
      "country": {
        "iso2Code": "no",
        "nameEn": "Norway",
        "nameNative": "Norge",
        "nameNo": "Norge"
      },
      "formatted": "Bjørnekroken 85\n1435 Ås",
      "formattedAddressLine1": "Bjørnekroken 85",
      "formattedAddressLine2": "1435 Ås",
      "formattedAddressLine3": "",
      "formattedAddressLine4": "",
      "formattedAddressLine5": "",
      "formattedAddressLine6": "",
      "postalCode": "1435"
    }
  }
```
