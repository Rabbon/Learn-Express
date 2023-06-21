# Markdown notes about express.js

## Basic Routing
**Routing** คือการกำหนดว่าจะให้ response อะไรตอบกลับ เมื่อมี request เข้ามาที่ server

```js
app.METHOD(PATH, HANDLER)
```
- **app** = ตัวแปรที่รับ express ไว้ใช้งาน
- **METHOD** = HTTP Request เช่น `get`, `post`, `put`, `patch`, `delete`
- **PATH** = path ของ server ที่ request จะเข้ามา
- **HANDLER** = function ที่จะตอบกลับเมื่อมีการ match request เข้ามา

## Route methods
```js
app.get('/', (req, res) => {
  res.send('GET requests to homepage')
})
```
เมื่อมีการ `GET` มาที่หน้า `/` ให้ response กลับไปว่า `GET request to homepage`

```js
app.post('/', (req, res) => {'
  res.send('POST request to homepage')
})
```
เมื่อมีการ `POST` มาที่หน้า `/` ให้ response กลับไปว่า `POST request to homepage`

## Route paths
กำหนดว่า request จะเข้ามาที่หน้าไหน เช่นหน้า `/home` path เป็น string หรือ regular expression ก็ได้

**ตัวอย่าง เช่น**
```js
app.get('/ab?cd', (req, res) => {
  res.send('ab?cd')
})
```
path นี้คือ `/acd`, `/abcd`

## Route parameters 
กำหนด parameters ของ path มีค่าอะไรก็ได้ ด้วยเครื่องหมาย `:` ก่อนหน้า path

**ตัวอย่าง เช่น**
```js
app.get('/users/:userId/books/:bookId', (req, res) => {
  res.send(req.params)
})
```
ถ้าเราส่ง request ไปที่ `/user/10/books/202`
ก็คือ เราคือ user id `10` ขอหนังสือเล่มที่ `202`

และอื่นๆ
```js
Route path: /flights/:from-:to
Request URL: http://localhost:3000/flights/LAX-SFO
req.params: { "from": "LAX", "to": "SFO" }
```

```js
Route path: /plantae/:genus.:species
Request URL: http://localhost:3000/plantae/Prunus.persica
req.params: { "genus": "Prunus", "species": "persica" }
```


