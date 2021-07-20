# BCC Members Data Access
This documentation is aimed at you as a developer/Technical Administrator for your organisation. The documentation here provides documentation on all the ways it is possible to integrate with BCC's membership system. 

url: https://members.bcc.no
swagger: https://members.bcc.no/docs

## Menu
[API integration](./api-integration.md)

## Actors
### Members
Members is the name for BCC's membership system. This is where all the members's data is residing
### Techinical Admin
The technical admin is a person that is registered in members that has a role called "Technical Administrator". This person has access to the system manage the client application for his organisation and to do things like applies for scopes etc. (Are you the tehcnical admin for your organisation? Write an email to it@bcc.no to get access for your organisation)
### Organization
All organisation that has a relationship to BCC, for example to get members personal data, will be registered in Members as an organisation
### Client
Organisation can have one or more applications registered attached to that organisation.
### Scope
A scope is a permission for your application for example 

## Setup
1. Write to it@bcc.no requesting the "Technical Administrator" role
2. Log into members.bcc.no and configure your application settings
3. In the application settings you can also apply for the scopes you require for your organisation
