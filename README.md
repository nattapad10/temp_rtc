# temp_rtc


![GitHub Logo](/img/1.png)

#Start Express
# index .js
```javascript
var mongoose = require('./config/mongoose');
var express = require('./config/express');
var cors = require('cors');
var db = mongoose();
var app = express();
var render = function(req, res) {

}
app.use(cors({origin: 'null'}));

app.use(function(req, res, next) {
  res.header("Access-Control-Allow-Origin", "*");
  res.header("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
  next();
});



app.listen(3010);
module.exports = app;

console.log('Server running at http://localhost:3010');

#สร้าง Schema ฐานข้อมูล
# temp_rtc.model.js
```javascript
var mongoose=require('mongoose');
var Schema=mongoose.Schema;

var tempSensorRTCSchema=new Schema({
    temperature: Number,
    humidity: Number,
    year: Number,
    month: Number,
    day: Number,
    hour: Number,
    minute: Number
});
const temp_rtc=mongoose.model('temp_rtc',tempSensorRTCSchema);
module.exports={temp_rtc}
```
#สร้าง route GET AND POST
# index.route.js
```javascript
module.exports = (app) => {
    var index = require('../controllers/data.controller');
    //app.get('/', index.render).post('/addData', index.addData).get('/data', index.getData);
    app.post('/addData', index.addData).get('/getData', index.getData).get('/', index.render);
    app.get('/humidity', index.humidity);

}
```





