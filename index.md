# BCC Members Data Access (BETA)
**NB: Please note that the members API is still in BETA, this means we still might make some changes to the data structure without versioning the API**
<br />
<br />
This documentation is aimed at you as a Developer/Technical Administrator for your organisation. The documentation here provides documentation on all the ways it is possible to integrate with BCC's membership system. 

**url: [https://members.bcc.no](https://members.bcc.no)** 
<br />
**swagger: [https://members.bcc.no/docs](https://members.bcc.no/docs)**

## Menu
- [Home](index.md)
- [API integration](api-integration.md)
- [Webhooks integration](webhooks.md)
- [Data Structures and Scopes](data-structures-and-scopes.md)

## Getting Started
1. Write to [it@bcc.no](mailto:it@bcc.no) requesting the "Technical Administrator" role
2. Log into [https://members.bcc.no](https://members.bcc.no) and configure your application settings
3. In the application settings you can also apply for the scopes you require for your [organisation](https://members.bcc.no/organisations)
4. You will be able use the scopes that has been approved for your application

# Concepts and Roles
### Members
"Members" is the name for BCC's membership system. This is where all the members's data is residing

### Techinical Admin
The technical admin is a person that is registered in members that has a role called "Technical Administrator". This person has access to the system to manage the application for his organisation and to do things like applies for scopes etc. _(Are you the tehcnical admin for your organisation? Write an email to [it@bcc.no](mailto:it@bcc.no) to get access for your organisation)_

### Organization
All organisations that has a relationship to BCC, for example because they are dependent on the members data, will be registered in Members as an organisation

### Application
An Organisation can have one or more applications registered that are attached to that organisation.

### Scope
A scope is a permission for your application for example the `members.read_membership` scope will give you access to read fields related to the members membership. See [Data Structures and Scopes](data-structures-and-scopes.md)


