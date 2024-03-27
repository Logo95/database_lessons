```json
db.users.drop()
true

show collections
articles
```

### Просмотр содержимого коллекции `articles`

```json
db.articles.find()
[ { _id: ObjectId('60fc24e87b8dc34ab172b51b'),
    author: 'author1',
    title: 'Exploring the Moon'
  },
  {
    _id: ObjectId('60fc24e87b8dc34ab172b51c'),
    author: 'author2',
    title: 'The Mysteries of Mars'
  },
  {
    _id: ObjectId('60fc24e87b8dc34ab172b51d'),
    author: 'author3',
    title: 'Journey through the Asteroid Belt'
  }
]
```

### Изменение первого документа в коллекции

```json
db.articles.findOneAndReplace({}, {'author': 'author0', 'title': 'The Secrets of Space Travel'})
{ _id: ObjectId('60fc24e87b8dc34ab172b51b'),
  author: 'author1',
  title: 'Exploring the Moon'
}

db.articles.find()
[ { _id: ObjectId('60fc24e87b8dc34ab172b51b'),
    author: 'author0',
    title: 'The Secrets of Space Travel'
  },
  {
    _id: ObjectId('60fc24e87b8dc34ab172b51c'),
    author: 'author2',
    title: 'The Mysteries of Mars'
  },
  {
    _id: ObjectId('60fc24e87b8dc34ab172b51d'),
    author: 'author3',
    title: 'Journey through the Asteroid Belt'
  }
]
```

### Удаление документа из коллекции

```json
db.articles.findOneAndDelete({}, {'author': 'author0'})
{ _id: ObjectId('60fc24e87b8dc34ab172b51b'),
  author: 'author0',
  title: 'The Secrets of Space Travel'
}

db.articles.find()
[ {
    _id: ObjectId('60fc24e87b8dc34ab172b51c'),
    author: 'author2',
    title: 'The Mysteries of Mars'
  },
  {
    _id: ObjectId('60fc24e87b8dc34ab172b51d'),
    author: 'author3',
    title: 'Journey through the Asteroid Belt'
  }
]
```

