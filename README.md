# Learn Express JS

## Membuat project baru

```console
$ mkdir myapp
$ cd myapp
$ npm init
$ sudo npm install express
```

## Membuat Hello World!

1. Buat file apps.js

```js
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
    res.send("Hello World!")
})
app.get('/:name', (req, res) =>{
    res.send(`Woy ${req.params.name}`)
})

app.listen(port, () => {
    console.log(`Example app listening at http://localhost:${port}`)
})
```

## Install nodemon agar tidak harus run-stop server

1. Cara install
```console
$ sudo npm install -g nodemon
```

2. Cara running
```console
$ nodemon apps.js
```

## Embedded Javascript Templates (Parsing Data)

Contohnya seperti ini `<%= anda! %>`

1. Install terlebih dahulu

```console
$ sudo npm install ejs
```

2. Cara pakai

Tambahkan code ini di apps.js

```js
app.set('views','./views')
app.set('view engine', 'ejs')

app.get('/', (req, res) => {
    const buah = [
        {name: "Apel"},
        {name: "Jeruk"},
        {name: "Semangka"},
    ]
    res.render('index',{
        nama: "Ahmad",
        buah: buah
    })
})
```

Buat file dan folder `views/index.ejs`

```ejs
<h1>Halo <%= nama %></h1>
```