# Data Structures and Scopes
This section describe `person` object and how it relates to scopes.

## Menu
- [Home](index.md)
- [API integration](api-integration.md)
- [Webhooks integration](webhooks.md)
- [Data Structures and Scopes](data-structures-and-scopes.md)

## Scopes
Currently Members supports the following scopes. (_To understand the concept of scopes please have a look at scopes section on the [Home](index.md) page_)
#### Identity (These scopes are consistent with [OIDC](https://openid.net/specs/openid-connect-core-1_0.html) scopes related to claims)
- `email`
- `phone`
- `profile - deprecated`
- `address`


#### Members (Custom Scopes)
- `members.read_person_id`
- `members.read_name`
- `members.read_birthdate - new`
- `members.read_gender - new`
- `members.read_culture - new`
- `members.read_picture - new`
- `members.read_church - new`
- `members.read_club - comming`
- `members.read_membership - deprecated`
- `members.read_spouse`
- `members.read_children_dependents - new`
- `members.read_parents_guardians - new`
- `members.read_family - deprecated`
- `members.read_orgs`

Once you have the "Technical Administrator" role ([See Getting Started](index.md)) you will be able to log in to members and apply for these scopes for your application. See [API integration](api-integration.md) it shows the navigation to your application.

## Data Structure
Currently these scopes are all related to the `person` object and maps to the person fields as follows...

###### By default you automatically get provided with the "personID" and "lastChangedDate" in the case where you get data related to the member.
```json
  {
    "personID": 54512,
    "lastChangedDate": "2021-07-16T12:41:10.168Z" 
  }
```
###### `members.read_person_id`
```json
  {
    "personID": 54512,   
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `email`
```json
  {
    "personID": 54512,
    "email": "philly.daly@gmail.com",
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
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
    },
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
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
    "gender": "Male",
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
    },
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `members.read_name`
```json
  {
    "personID": 54512,
    "firstName": "Philly",
    "middleName": "Pelle",
    "lastName": "Daly",
    "displayName": "Philly Pelle Daly",
    "lastChangedDate": "2021-07-16T12:41:10.168Z"   
  }
```
###### `members.read_birthdate`
```json
  {
    "personID": 54512,    
    "birthDate": "1988-12-08T00:00:00",    
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `members.read_culture`
```json
  {
    "personID": 54512,    
    "cultureCode1": "en-US",    
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `members.read_picture`
```json
  {
    "personID": 54512,    
    "profilePicture": "https://storage.googleapis.com/kinetic-center-276213_profile-pictures/178509735_a0mdd0q2qh.jpg",
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `members.read_church`
Caution: `church.org` property is deprecated and will be removed soon
```json
  {
    "personID": 54512,
    "churchID": 69,
    "church": {
      "active": true,
      "archived": false,
      "startDate": "2020-10-18T11:52:46.474Z",
      "endDate": "2021-11-28T00:00:00.000Z",
      "name": "Oslo/Follo",
      "visitingAddress": {
        "address1": "Ryenstubben 2",
        "address2": "0679 Oslo",
        "address3": null,
        "address4": null,
        "city": null,
        "country": {
          "iso2Code": "no",
          "nameEn": "Norway",
          "nameNative": "Norge",
          "nameNo": "Norge"
        },
        "postalCode": 1444
      },
      "orgID": 69,
      "org": {
        "churchID": 69,
        "name": "Oslo/Follo",
        "orgID": 69,
        "visitingAddress": {
          "address1": "Ryenstubben 2",
          "address2": "0679 Oslo",
          "address3": null,
          "address4": null,
          "city": null,
          "country": {
            "iso2Code": "no",
            "nameEn": "Norway",
            "nameNative": "Norge",
            "nameNo": "Norge"
          },
          "postalCode": 1444
        }
      }
    },
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `members.read_membership`
Caution: `church.org` property is deprecated and will be removed soon
```json
  {
    "personID": 54512,
    "churchID": 69,
    "church": {
      "active": true,
      "archived": false,
      "startDate": "2020-10-18T11:52:46.474Z",
      "endDate": "2021-11-28T00:00:00.000Z",
      "name": "Oslo/Follo",
      "visitingAddress": {
        "address1": "Ryenstubben 2",
        "address2": "0679 Oslo",
        "address3": null,
        "address4": null,
        "city": null,
        "country": {
          "iso2Code": "no",
          "nameEn": "Norway",
          "nameNative": "Norge",
          "nameNo": "Norge"
        },
        "postalCode": 1444
      },
      "orgID": 69,
      "org": {
        "churchID": 69,
        "name": "Oslo/Follo",
        "orgID": 69,
        "visitingAddress": {
          "address1": "Ryenstubben 2",
          "address2": "0679 Oslo",
          "address3": null,
          "address4": null,
          "city": null,
          "country": {
            "iso2Code": "no",
            "nameEn": "Norway",
            "nameNative": "Norge",
            "nameNo": "Norge"
          },
          "postalCode": 1444
        }
      }
    },
    "lastChangedDate": "2021-07-16T12:41:10.168Z"
  }
```
###### `members.spouse`
Caution: `church.org` property is deprecated and will be removed soon
```json
  {
    "personID": 54512,
    "related": {
      "spouse": [
        {        
          "personID": 13629
        }
      ]
    }
  }
```
###### `members.read_children_dependents`
```json
  {
    "personID": 54512,
    "related": {
      "children": [
        {          
          "personID": 13623
        }
      ],      
      "dependents": [
        {          
          "personID": 16633
        }
      ]     
    }
  }
```
###### `members.read_parents_guardians`
```json
  {
    "personID": 54512,
    "related": {
      "parents": [
        {          
          "personID": 13624
        }
      ],      
      "guardians": [
         {          
          "personID": 14654
        }
      ]     
    }
  }
```
###### `members.read_family`
Caution: `church.org` property is deprecated and will be removed soon
```json
  {
    "personID": 54512,
    "related": {
      "spouse": [
        {
          "church": {
            "orgID": 69,
            "org": {
              "churchID": 69
            }
          },
          "displayName": "Batie Sofa Daly",
          "personID": 13629
        }
      ],
      "children": [...],
      "dependents": [...],
      "guardians":[...],
      "parents": [...]
    }
  }
```
###### `mmembers.read_orgs`
```json
{  
  "name": "Oslo/Follo",
  "orgID": 69,
  "status": 0,
  "type": "church",
  "visitingAddress": {
    "country": {
      "iso2Code": "no",
      "nameEn": "Norway",
    }
  },
  "website": null
}
```
