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
- `profile`
- `email`
- `address`
- `phone`

#### Members (Custom Scopes)
- `members.read_membership`
- `members.read_family`

Once you have the "Technical Administrator" role ([See Getting Started](index.md)) you will be able to log in to members and apply for these scopes for your application. See [API integration](api-integration.md) it show how to get access to your application.

## Data Structure
Currently these scopes are all related to the `person` object and looks maps to the scopes as follows

