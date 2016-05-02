# Negotia visma

Dette repoet er primært en [issue tracker](https://github.com/ItemConsulting/negotia-visma-open/issues), for å kommunisere rundt Negotia/Visma integrasjonen.

## Returns the member representation of a user

`GET /api/members/{member-id}`

| Http status code | Body                   |
|------------------|------------------------|
| 200              | `Member repesentation` |


## Return a list of groups the member is attached to

`GET /api/members/{member-id}/groups`

| Http status code | Body                        |
|------------------|-----------------------------|
| 200              | Array `Group repesentation` |

## Return a list of members of a group

`GET /api/members/{member-id}/groups/{group-id}`

| Http status code | Body                         |
|------------------|------------------------------|
| 200              | Array `Member repesentation` |

## Member repesentation

```javascript
{
  "id": 201234,
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
  "email": "rex@slottet.no",
  "birthday": "1937-02-21T13:02:00Z",
  "memberSince": "1995-05-30T12:03:00Z",
}
```

## Group repesentation

```javascript
{
  "id":9,
  "position":"Konsern/hovedtillitsvalgt",
  "organization":"Fubar AS"
}
```

