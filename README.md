# Okta-Scim-Server

Sample SCIM server written in Node.js. It can be used with SCIM app in Okta for getting SCIM messages related to user provisioning. It supports following Users endpoints

1) Create User (POST to {SCIM Base Url}/User)
2) Get Users (GET to {SCIM Base Url}/User)
3) Get User By Id (POST to {SCIM Base Url}/User/:UserId)
4) Deactivate User (PATCH to {SCIM Base Url}/User/:UserId)
5) Modify/Update User (PUT to SCIM Base Url}/User/:UserId)

# Installation

Download and run "npm install"

# Running and Testing the Server

Once all above is install run the node server "npm start". Make the following cals from any REST Client (Postman, cURL etc,) or API validation tools Runscope.

You can use ngrok "ngrok http 8081" to make server available online. use https://abc.ngrok.io in Okta SCIM app or Runscope to test online. 

1) `POST {SCIM_Base_Url}/scim/v2/Users`

```json
{
   "schemas": [
      "urn:ietf:params:scim:schemas:core:2.0:User"
   ],
   "userName": "username@example.com",
   "name": {
      "givenName": "<GivenName>",
      "middleName": "",
      "familyName": "<FamilyName>"
   },
   "emails": [
      {
         "primary": true,
         "value": "username@example.com",
         "type": "work"
      }
   ],
   "displayName": "<display name>",
   "externalId": "<externalId>",
   "groups": [],
   "active": true
}
```

2) `GET {SCIM_Base_Url}/scim/v2/Users?count=2&startIndex=1`

3) `GET {SCIM_Base_Url}/scim/v2/Users?count=1&filter=userName eq "username@example.com"&startIndex=1`

4) `PUT {SCIM_Base_Url}/scim/v2/Users/<UserID>`

```json
{
  "schemas": [
    "urn:ietf:params:scim:schemas:core:2.0:User"
  ],
  "id": "a5222dc0-4dec-11e6-866c-5b600f3e2809",
  "userName": "username@example.com",
  "name": {
    "givenName": "<GivenName>",
    "middleName": "undefined",
    "familyName": "<FamilyName>"
  },
  "active": "true",
  "meta": {
    "resourceType": "User",
    "location": "<location uri>"
  },
  "emails": [
    {
      "primary": true,
      "type": "work",
      "value": "username@example.com"
    }
  ],
  "displayName": "<display Name>",
  "externalId": "<externalId>",
  "groups": []
}
```

  5) `PATCH {SCIM_Base_Url}/scim/v2/Users/<UserID>`

```json
{
   "schemas":["urn:ietf:params:scim:api:messages:2.0:PatchOp"],
   "Operations":[{"op":"replace","value":{"active":true}}]
}
```

