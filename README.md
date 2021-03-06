# Negotia visma

Dette repoet er primært en [issue tracker](https://github.com/ItemConsulting/negotia-visma-open/issues), for å kommunisere rundt Negotia/Visma integrasjonen.

### Authentication
Authentication: BASIC – Uses an admin user/pass for all calls

## REST Endpoints

### 1. ~~Returns the member representation of a user~~

`GET /api/members/{member-id}`

| Http status code | Body                   |
|------------------|------------------------|
| 200              | `Member repesentation` |


### 2. ~~Return a list of groups the member is attached to~~

`GET /api/members/{member-id}/groups`

| Http status code | Body                        |
|------------------|-----------------------------|
| 200              | Array `Group repesentation` |

### 3. ~~Return a list of members of a group~~

`GET /api/members/{member-id}/groups/{group-id}`

| Http status code | Body                         |
|------------------|------------------------------|
| 200              | Array `Member repesentation` |

### 4. ~~Return a list of members that has left a group~~

Add a `memberUntil`-field to the `Member representation` json-object.

`GET /api/members/{member-id}/groups/{group-id}/status/@left-recently`

| Http status code | Body                         |
|------------------|------------------------------|
| 200              | Array `Member repesentation` |

### 5. ~~Return a list of files~~

`GET /api/members/{member-id}/files`

| Http status code | Body                         |
|------------------|------------------------------|
| 200              | Array `File repesentation`   |

### 6. ~~Return file as binary~~

`GET /api/members/{member-id}/files/{file-id}`

Should return with the `Content-Type` header set. It should have the mime type (e.g. `application/pdf` or `application/vnd.ms-excel`), or `application/octet-stream` if unknown mime type.

According to [Stackoverflow](http://stackoverflow.com/questions/10725959/file-transfer-over-http), the body of the response is binary, not base64.

| Http status code | Body                               |
|------------------|------------------------------------|
| 200              | Binary representation of the file  |
| 403 (forbidden)  | *empty*                            |

### 7. Return a list of scolorship application status'

`GET /api/members/{member-id}/scholarship`

| Http status code | Body                                |
|------------------|-------------------------------------|
| 200              | Array `Scholarship repesentation`   |

## Return objects

### Member repesentation

```javascript
{
  "id": "201234",
  "firstName": "Harald",
  "lastName": "Rex",
  "address1": "",
  "address2": "Slottsplassen 1",
  "address3": "",
  "zipCode": "0010",
  "city": "OSLO",
  "countryId": "0",
  "countryName": "Norway",
  "privateAddress": "",
  "phoneWork": "",
  "phoneMobile": "12341234",
  "phonePrivate": "",
  "email": "post@slottet.no",
  "birthday": "1937-02-21T13:02:00Z", // ISO 8601
  "memberSince": "1995-05-30T12:03:00Z",
  "memberUntil" : "2016-06-14T11:15:00Z",
  // new fields 2016-06-22
  "workplace": "Revisorbrødrene AS", // Arbeidsted
  "representativeCompanyId": 301, // TV arbeidsgiver
  "representativeCompanyTitle": "Tillitsvalgt",
  "representativeWorkplaceId": 302, // TV arbeidssted
  "representativeWorkplaceTitle": "Vara Tillitsvalgt",
  "lastLoginDate": "2016-06-20T12:04:00Z",
  "totalLogins": 204,
  "department": "", // Lokalavdeling
  "memberStatus": "", // Medlemstatus
  "paymentMethod": "Lønnstrekk"
}
```

### Group repesentation

```javascript
{
  "id": "9@35",
  "position":"Konsern/hovedtillitsvalgt",
  "organization":"Fubar AS"
}
```

### File representation

```javascript
{
  "id": "5075082",
  "name": "Dørskilt nye.docx",
  "created": "2015-08-19T00:00:00Z"
}
```

### Scholarship-application representation

```javascript
{
  "id": "5075082",
  "name": "Dørskilt nye.docx",
  "created": "2015-08-19T00:00:00Z"
}
```
