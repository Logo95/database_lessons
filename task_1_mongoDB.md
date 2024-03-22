## Collections and Documents

### `users` Collection

```json
[
  {
    "_id": "1",
    "login": "novelist",
    "name": "Mary Shelley",
    "email": "mary@example.com"
  },
  {
    "_id": "2",
    "login": "poet",
    "name": "Edgar Allan Poe",
    "email": "edgar@example.com"
  }
]
```

### `messages` Collection
```json
[
  {
    "_id": "101",
    "login": "novelist",
    "message": "It is true, we shall be monsters, cut off from all the world..."
  },
  {
    "_id": "102",
    "login": "poet",
    "message": "All that we see or seem is but a dream within a dream."
  },
  {
    "_id": "103",
    "login": "novelist",
    "message": "Beware; for I am fearless, and therefore powerful."
  }
]
```

### Aggregation Query
```json
db.users.aggregate([
  {
    $lookup: {
      from: "messages",
      localField: "login",
      foreignField: "login",
      as: "user_messages"
    }
  }
])
```

### Aggregation Result
```json
{
  "_id": "1",
  "login": "novelist",
  "name": "Mary Shelley",
  "email": "mary@example.com",
  "user_messages": [
    {
      "_id": "101",
      "login": "novelist",
      "message": "It is true, we shall be monsters, cut off from all the world..."
    },
    {
      "_id": "103",
      "login": "novelist",
      "message": "Beware; for I am fearless, and therefore powerful."
    }
  ]
}
