`server.js`
```javascript
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;
const ejs = require('ejs');
const path = require('path');

// Define paths to configure Express
const publicDirPath = path.join(__dirname, './public');
const viewsPath = path.join(__dirname, './views');

//setup ejs engine and views location
// set the view engine to ejs
app.set('view engine', 'ejs');
app.set('views', viewsPath); //By default its paths is setted to '../views' as folder name

//setup static directory to serve
app.use(express.static(publicDirPath));

// index page
app.get('/', (req, res) => {
	res.render('pages/index', {
		heading: 'Home'
	});
});

// about page
app.get('/products', (req, res) => {
	res.render('pages/products', {
		heading: 'Products'
	});
});

// 404 Page
app.get('*', (req, res) => {
	res.render('pages/404', {
		heading: 'Error 404',
		message: 'Page Not Found!'
	});
});

app.listen(port, () => {
	console.log('Server has been started on the port ', port);
});

```