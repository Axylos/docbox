## Trains


You can `create`, `update`, and `delete` your trains as well as `get` a list of all trains or `get` a list of just your trains.


Choo Choo

### List trains

Lists all trains.  

```endpoint
GET /trains
```

#### Example request

```curl
$ curl http://wdi_friends.draketalley.com/api/trains \
		-H 'Authorization: Bearer asjkhdfkjhdf-384394-asdfkhasdkjf'
```


```javascript
api.get('/trains');
```


#### Example response

```json
[
  {
    "id": "b3850751-e1c5-4a6c-9b3e-18ef2a1a3885",
    "name": "Thomas",
    "km_traveled": 0,
    "train_type": "Locomotive",
    "user_id": "305b9d34-e959-4d5c-98a9-1cdefb0fa8d0",
    "created_at": "2019-02-19T19:00:48.936Z",
    "updated_at": "2019-02-19T19:00:48.936Z"
  },
  {
    "id": "333fdb0a-4531-4d13-b2f4-fe58b1caaa5b",
    "name": "chugga chugga",
    "km_traveled": 1000,
    "train_type": "choo choo",
    "user_id": "6954c467-0f29-49e2-8e4e-f087753360b6",
    "created_at": "2019-04-19T15:47:06.916Z",
    "updated_at": "2019-04-19T15:47:06.916Z"
  }
]
```

### Create train

Creates a new train.

```endpoint
POST /trains
```

#### Example request

```curl
curl http://wdi_friends.draketalley.com/api/trains \
  -X POST \
  -H 'Authorization: Bearer asjkhdfkjhdf-384394-asdfkhasdkjf' \
  -H 'Content-Type: application/json' \
  -d '{"name": "Neville", "train_type": "Diesel", "km_traveled": 34012}'
```



```javascript
await api.post('/trains', {
  name: 'Neville',
  train_type: 'Diesel',
  km_traveled: 5003
});
```



#### Example request body

```json
{
  "name": "Neville",
  "train_type": "Diesel",
  "km_traveled": 5003
}
```

Property | Description
---|---
`name` | the name of the train
`train_type` | the type of the train
`km_traveled` | distance traveled in kilometers

#### Example response

```json
{
  "id": "086a3fcd-19b7-42b8-8a5d-afb82cdb81b2",
  "name": "Neville",
  "km_traveled": 5003,
  "train_type": "Diesel",
  "user_id": "305b9d34-e959-4d5c-98a9-1cdefb0fa8d0",
  "created_at": "2019-04-23T19:22:09.723Z",
  "updated_at": "2019-04-23T19:22:09.723Z"
}
```


### Update a train

Updates the properties of a particular train.

```endpoint
PUT /trains/{train_id}
```

#### Example request

```curl
curl http://wdi_friends.draketalley.com/api/trains/a63fd254-3c2c-4ff5-b9ad-2c0192de6aab \
  -X PUT \
  -H 'Authorization: Bearer asjkhdfkjhdf-384394-asdfkhasdkjf' \
  -H 'Content-Type: application/json' \
  -d '{"name": "Nellie", "train_type": "Steam", "km_traveled": 3403894}'
```



```javascript
await api.put('/trains/a63fd254-3c2c-4ff5-b9ad-2c0192de6aab', {
  name: 'Nellie',
  train_type: 'Steam',
  km_traveled: 8023
});
```

#### Example request body

```json
{
  "name": "Nellie",
  "train_type": "Steam",
  "km_traveled": 8023
}
```

Property | Description
---|---
`name` | the name of the train
`train_type` | the type of the train
`km_traveled` | distance traveled in kilometers

#### Example response

```json
{
  "user_id": "305b9d34-e959-4d5c-98a9-1cdefb0fa8d0",
  "id": "a63fd254-3c2c-4ff5-b9ad-2c0192de6aab",
  "name": "Nellie",
  "train_type": "Steam",
  "km_traveled": 8023,
  "created_at": "2019-04-23T19:28:47.962Z",
  "updated_at": "2019-04-23T19:34:57.222Z"
}
```

### Delete a train

Deletes a train.  Must be authenticated as the user identified by "user_id" in order to delete a particular train

```endpoint
DELETE /trains/{train_id}
```

#### Example request

```curl
curl http://wdi_friends.draketalley.com/api/trains/a63fd254-3c2c-4ff5-b9ad-2c0192de6aab \
	-H 'Authorization: Bearer asjkhdfkjhdf-384394-asdfkhasdkjf' \
	-X DELETE 
```



```javascript
api.delete('/trains/a63fd254-3c2c-4ff5-b9ad-2c0192de6aab');
```


### List current user trains

List all the trains that belong to the authenticated user

```endpoint
GET /trains/user
```

#### Example request

```curl
curl http://wdi_friends.draketalley.com/api/trains/user \
  -H 'Authorization: Bearer asjkhdfkjhdf-384394-asdfkhasdkjf'
```



```javascript
api.get('/trains/user');
```

#### Example response

```json
[
  {
    "id": "b3850751-e1c5-4a6c-9b3e-18ef2a1a3885",
    "name": "Thomas",
    "km_traveled": 0,
    "train_type": "Locomotive",
    "user_id": "305b9d34-e959-4d5c-98a9-1cdefb0fa8d0",
    "created_at": "2019-02-19T19:00:48.936Z",
    "updated_at": "2019-02-19T19:00:48.936Z"
  },
  {
    "id": "8b8961d3-cd11-47d0-9753-1c526ce4edf8",
    "name": "GSL caboose",
    "km_traveled": 1,
    "train_type": "caboose",
    "user_id": "305b9d34-e959-4d5c-98a9-1cdefb0fa8d0",
    "created_at": "2019-02-22T15:16:17.133Z",
    "updated_at": "2019-02-22T15:16:17.133Z"
  }
]
```