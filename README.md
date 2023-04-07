var express = require('express');
var app = express();
const path = require('path');

var cors = require('cors');
app.use(cors());

//app.use('/static', express.static('public'));
app.use('/static', express.static(path.join(__dirname, '/Storage/3DAssets')))
console.log('started on port 3004')

app.listen(3004);
