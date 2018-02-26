# Node-Red-MongoDB

Node Red with MongoDB
- Insert
- Read
- Update

![Bild 1](https://raw.githubusercontent.com/ToWipf/Node-Red-MongoDB/master/MongoNodes.PNG)

``` JavaScript
[{"id":"b5294d2c.c44d08","type":"mongodb out","z":"8e62bd6f.a2b1a","mongodb":"127827e8.d72bd","name":"","collection":"test","payonly":false,"upsert":false,"multi":false,"operation":"store","x":890,"y":240,"wires":[]},{"id":"9fc42432.ae52d","type":"inject","z":"8e62bd6f.a2b1a","name":"ADD firstPayload","topic":"233","payload":"firstPayload","payloadType":"str","repeat":"","crontab":"","once":false,"x":433,"y":240,"wires":[["b5294d2c.c44d08"]]},{"id":"2a8cd61b.ab2cea","type":"mongodb out","z":"8e62bd6f.a2b1a","mongodb":"127827e8.d72bd","name":"","collection":"test","payonly":false,"upsert":false,"multi":false,"operation":"store","x":890,"y":320,"wires":[]},{"id":"f31eae67.61d47","type":"inject","z":"8e62bd6f.a2b1a","name":"ADD firstPayload","topic":"Topic","payload":"Payload","payloadType":"str","repeat":"","crontab":"","once":false,"x":433,"y":320,"wires":[["b29c1e75.89ed2"]]},{"id":"b29c1e75.89ed2","type":"function","z":"8e62bd6f.a2b1a","name":"","func":"msg.payload = msg.payload;\nmsg.spalte2 = 'XXXX';\nmsg.spalte4 = msg.payload;\nreturn msg;","outputs":1,"noerr":0,"x":650,"y":320,"wires":[["2a8cd61b.ab2cea"]]},{"id":"782c8d73.699814","type":"inject","z":"8e62bd6f.a2b1a","name":"","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":400,"y":440,"wires":[["8beecd14.1a5a6"]]},{"id":"8be095c0.584c18","type":"debug","z":"8e62bd6f.a2b1a","name":"A","active":true,"console":"false","complete":"payload","x":970,"y":440,"wires":[]},{"id":"6d25c58d.b52f6c","type":"function","z":"8e62bd6f.a2b1a","name":"","func":"var last = msg.payload.length;\n\n//for (i = 0; i < msg.payload.length; i++)\n//{\n//    test = msg.payload[i].temp\n//}\nmsg.payload = msg.payload[5].temp\n\nreturn msg;","outputs":1,"noerr":0,"x":810,"y":440,"wires":[["8be095c0.584c18"]]},{"id":"bfce8122.c9759","type":"debug","z":"8e62bd6f.a2b1a","name":"B","active":false,"console":"false","complete":"payload[5].temp","x":970,"y":500,"wires":[]},{"id":"8beecd14.1a5a6","type":"mongodb in","z":"8e62bd6f.a2b1a","mongodb":"127827e8.d72bd","name":"","collection":"temps","operation":"find","x":610,"y":440,"wires":[["bfce8122.c9759","6d25c58d.b52f6c"]]},{"id":"6a553c6.d6a7244","type":"comment","z":"8e62bd6f.a2b1a","name":"Lesen","info":"","x":340,"y":380,"wires":[]},{"id":"c3090b58.61ef6","type":"comment","z":"8e62bd6f.a2b1a","name":"Schreiben","info":"","x":360,"y":180,"wires":[]},{"id":"9cf77c76.165d9","type":"mongodb out","z":"8e62bd6f.a2b1a","mongodb":"127827e8.d72bd","name":"","collection":"settings","payonly":false,"upsert":false,"multi":false,"operation":"update","x":840,"y":600,"wires":[]},{"id":"cd2f78.621b5088","type":"function","z":"8e62bd6f.a2b1a","name":"Letztes Pumpen um","func":"var tmp = {};\n//tmp.value = Date.now();\n//tmp.name = \"last_gies\";\n//tmp.projection = {\"name\": \"last_gies\"};\ntmp.query = {\"name\" : \"licht_aus\"};\ntmp.payload = {\"name\" : \"licht_aus\", \"value\": \"18:00\"};\nreturn tmp;","outputs":1,"noerr":0,"x":600,"y":600,"wires":[["9cf77c76.165d9"]]},{"id":"ea7f712b.1262a","type":"comment","z":"8e62bd6f.a2b1a","name":"update","info":"","x":350,"y":540,"wires":[]},{"id":"502a835b.ac0794","type":"inject","z":"8e62bd6f.a2b1a","name":"","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":400,"y":600,"wires":[["cd2f78.621b5088"]]},{"id":"127827e8.d72bd","type":"mongodb","z":"","hostname":"127.0.0.1","port":"27017","db":"greenhouse","name":"greenhouse"}]
```

Node Red Code
