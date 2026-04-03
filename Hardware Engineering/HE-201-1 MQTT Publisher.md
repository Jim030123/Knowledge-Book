```js
const mqtt = require("mqtt")
const mysql = require("mysql2")

const client = mqtt.connect("mqtt://localhost")

const db = mysql.createConnection({
 host:"localhost",
 user:"root",
 password:"",
 database:"iot"
})

client.on("connect", ()=>{

 console.log("MQTT connected")

 client.subscribe("chiller/temperature")

})

client.on("message",(topic,message)=>{

 let temp = message.toString()

 console.log("Temperature:",temp)

 db.query(
  "INSERT INTO temperature_logs_file (sensor_id,position,temperature,alert_status) VALUES (1,'Chiller',?,0)",
  [temp]
 )

})
```

Node JS