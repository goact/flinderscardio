# Health Information related User account
  

## 1. POST /mint/api/v1/user/health/:accessToken

Store Persional Health Information (PHI) fields into the goAct database. 

### Authentication

Request must be authenticated by an Application specific token.

### Example Request

Requested data should be JSON array.  

```sh
curl -i -H "Content-Type: application/json" -H "Authorization: ApplicationToken 1YotnFZsEjr1zCsicMWpAAFSa" -X POST -d '[{"accessType" : "add", "firstName" : "Firstname", "lastName" : "Lastname", "age" : 33, "sex" : "F", "height" : 178, "weight" : 75, "bmi" : 75, "smoking" : 75, "alcoholConsumption" : 75 , "conceiveTry" : 75, "conceiveTryMonthly" : 75, "healthyBaby" : true, "sti" : true, "stiPositive" : false, "menstruation" : true, "havingSex" : 10, "havingSexMultiple" : 'unsure', "contraception" : true, "medicalConditions" : ["Diabetes","Endometriosis"] }]'  https://flinderscardio.goact.co/mint/api/v1/health/dbd4bc88-7f44-4cd7-b9f6-06db922e36c2
```
### Example Response 1 if user health information has already been added.

```javascript
{ 
  "code": "200"
  "added" : 1
}
```

### Example Response 2 if user hasn't been added .

```javascript
{ 
  "error" : "500",
  "description" : "The server encountered an unexpected error"
}
```

If the field value is not set, it is **null**.

### Fields

Fields that belong to the user account

Field | Description
---------|-------- 
accessType  | 'new' or 'add'. **Must not be null**. new - for new visitor who has no cookie. add - for visitor who has cookie or logged in user.
accessToken | goAct access token for this user. **Must not be null** if accessType is 'add'. Response **Must not be null** . For anonymous user it should be set with visitor ID
age | *Optional* User's age.
sex | *Optional* Biological sex. Choises are "M" for male, "F" for female or null.
weight |    *Optional* Weight in kilograms
height |    *Optional* Height in centimeters  
smoking |  *Optional* Response for Cigarettes per day. 
alcoholConsumption |  *Optional* Response for Standard drinks per week. 
field_name1 | Response for field_name1 ( It can be replaced with a field name).
field_name2 | Response for field name2 ( It can be replaced with a field name). 
field_name3 | Response for field name3 ( It can be replaced with a field name). 
field_name3 | Response for field name4 ( It can be replaced with a field name). 
... | 
... | 
... | 
code | 200 - success code
added | The number of inserted responses into database.
 
 







