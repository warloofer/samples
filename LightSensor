var mqtt = require('mqtt');
//console.log("Connecting to MQTT broker...");
var mqtt = require('mqtt');
var options = {
	port: 1883,
	host: '192.168.1.8',
	clientId: 'LuzAmbiente'
};
var client = mqtt.connect(options);
console.log("Connected to MQTT broker");
client.subscribe('LuzAmbiente');
client.on('message', function(topic, msg) 
{
	if (msg == 'Status ON')
	{
		console.log('Luz Ambiente Status is 4000');
		ITEM_LOCAL.item_value = 4000;
		item
			.getService(Service.LightSensor )
			.getCharacteristic(Characteristic.CurrentAmbientLightLevel, 4000);
	}	
		
	
});

var Accessory = require('../').Accessory;
var Service = require('../').Service;
var Characteristic = require('../').Characteristic;
var uuid = require('../').uuid;


var ITEM_LOCAL = 
{ 
	item_value: 4000
}


var accessory_ID = uuid.generate('hap-nodejs:accessories:item');
var item = exports.accessory = new Accessory('Luz Ambiente', accessory_ID);
item.username = "00:00:00:00:00:04"; 
item.pincode = "987-65-432";

item
	.getService(Service.AccessoryInformation)
	.setCharacteristic(Characteristic.Manufacturer, "Fran")
	.setCharacteristic(Characteristic.Model, "Rev-1")
	.setCharacteristic(Characteristic.SerialNumber, "0000004");


item.on('identify', function(paired, callback) 
	{
		console.log("Identify the Luz Exterior!");
		callback(); // success
	});


item
	.addService(Service.LightSensor , "Luz Ambiente") // services exposed to the user should have "names" like "Fake Light" for us
	.getCharacteristic(Characteristic.CurrentAmbientLightLevel, 4000);
	
item
	.getService(Service.LightSensor)
	.getCharacteristic(Characteristic.CurrentAmbientLightLevel)
	.on('get', function(callback) 
	{
   
		var err = null; // in case there were any problems
		callback(err, ITEM_LOCAL.item_value);
			
	});

