[notes](notes.md) | [backend](backend.md)

## Server-Side
- [databases](databases.md)
- [express.js](javascript/express.md)
- [linux terminal](linux/terminal.md)
- [node.js](javascript/node.md)
- [security](security.md)

### CRUD/ REST API's
Create, Read, Update, Destroy.. See [SQL](../SQL.md)

`POST /tweets`: To post a new tweet

`GET /tweets`: To see all tweets

`GET /tweets/:id`: To see a particular tweet

`PUT /tweets/:id`: Replace whole object

`PUT /tweets/7 {color: 'blue'}` => `{id: 7, color: 'blue'}`

`PATCH /tweets/:id` ( replace part of object ) `{id: 7, tweet: 'hi', color: 'red'}`

`PATCH /tweets/7 {color: 'blue'}` =>  `{id: 7, tweet: 'hi', color: 'blue'}`

`DELETE /tweets/:id`: Delete a particular tweet


---

### Links
- http://code-maven.com

See also [asynchronous](async.md) | [client-side](client-side.md) | [networks](networks/index.md)
