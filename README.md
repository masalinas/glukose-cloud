# Glukose Cloud

A SaaS to concentrate all glucose measures using node-RED IBM message broker and MQTT IBM protocol to comunicate with the Glukose Gateways.

![glukose_cloud_app](https://cloud.githubusercontent.com/assets/1216181/14146100/c60518c0-f696-11e5-93e1-1eb91aaceb3f.png)

The Cloud node-RED Designer

![glukose-cloud-node](https://cloud.githubusercontent.com/assets/1216181/14145935/169d0f0a-f696-11e5-8575-b1fbdc457ebd.png)

# Infraestructure Techonologies:

- [NodeJS](https://nodejs.org/): Event-driven I/O server-side JavaScript environment based on V8. Includes API documentation, change-log, examples and announcements.
- [ExpressJS](http://expressjs.com): Express is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.
- [MongoDb](https://www.mongodb.org/):MongoDB is the next-generation database that lets you create applications never before possible.
- [Node-Red](http://nodered.org/): A visual tool for wiring the Internet of Things.

# Backend Techonologies:

- [Loopback](https://strongloop.com/): LoopBack is a highly-extensible, open-source Node.js framework. Compare with other frameworks. Quickly create dynamic end-to-end REST APIs.
- [socket.io](http://socket.io/): Socket.IO enables real-time bidirectional event-based communication.
- [MomentJs](http://momentjs.com/): Parse, validate, manipulate, and display dates in JavaScript.

# Frontend Techonologies:

- [RequireJS](http://requirejs.org/): RequireJS is a JavaScript file and module loader.
- [Require DomReady](https://github.com/requirejs/domReady): An AMD loader plugin for detecting DOM ready.
- [JQuery](https://jquery.com): jQuery: The Write Less, Do More, JavaScript Library.
- [JQuery UI](https://jqueryui.com/): jQuery UI is a curated set of user interface interactions, effects, widgets, and themes built on top of the jQuery JavaScript Library.
- [Angular](https://angularjs.org): AngularJS is what HTML would have been, had it been designed for building web-apps.
- [Angular Couch Potato](https://github.com/laurelnaiad/angular-couch-potato): Lazy-Load and Register Components in AngularJS Applications.
- [Angular Resource](https://github.com/angular/bower-angular-resource): A factory which creates a resource object that lets you interact with RESTful server-side data sources.
- [Angular UI Router](https://github.com/angular-ui/ui-router): The de-facto solution to flexible routing with nested views in AngularJS.
- [Angular Animate](https://angularjs.org): AngularJS provides animation hooks for common directives.
- [Angular Bootstrap](https://angular-ui.github.io/bootstrap/): Bootstrap components written in pure AngularJS by the AngularUI Team.
- [angular-socket-io](https://github.com/btford/angular-socket-io): Socket.IO component for AngularJS.
- [angular-toastr](https://github.com/Foxandxss/angular-toastr):Angular port of CodeSeven/toastr.
- [socket.io](http://socket.io/): Socket.IO enables real-time bidirectional event-based communication.
- [Bootstrap](http://getbootstrap.com/): Bootstrap, a sleek, intuitive, and powerful mobile first front-end framework for faster and easier web development.
- [DarkVelvet](http://pixelkit.com/): Free UI Kits built on Bootstrap for any developer that wants to build a cool looking and functional website.
- [MomentJs](http://momentjs.com/): Parse, validate, manipulate, and display dates in JavaScript.
- [Datatable](https://datatables.net/): DataTables is a plug-in for the jQuery Javascript library.

# Installation:

Execute npm to install node packages:
```
  npm install
```

Execute bower to install ui packages:
```
  bower install
```

Access Web Glukose
```
  http://localhost:2000
```

Access Web Glukose JSON API Back-end
```
  http://localhost:2000/export
```

Access Node-Red Web designer
```
  http://localhost:2000/red
```

Copy and import this flow from node-red import clipboard
```
[{"id":"4d1060c0.b2efa","type":"mqtt-broker","z":"f2181939.0de7e8","broker":"localhost","port":"1883","clientid":"","usetls":false,"verifyservercert":true,"compatmode":true,"keepalive":"60","cleansession":true,"willTopic":"","willQos":"0","willRetain":"false","willPayload":"","birthTopic":"","birthQos":"0","birthRetain":"false","birthPayload":""},{"id":"9a3f0709.65c0f8","type":"debug","z":"f2181939.0de7e8","name":"out debug","active":true,"console":"false","complete":"payload","x":457,"y":60,"wires":[]},{"id":"ec611d7f.139ee","type":"catch","z":"f2181939.0de7e8","name":"","scope":null,"x":190,"y":222,"wires":[["bb6a5bca.4495a8"]]},{"id":"bb6a5bca.4495a8","type":"debug","z":"f2181939.0de7e8","name":"error","active":true,"console":"false","complete":"payload","x":356,"y":222,"wires":[]},{"id":"cbec3d13.3413c","type":"function","z":"f2181939.0de7e8","name":"persist","func":"console.log('Start persist node');\n\nvar loopback = context.global.loopback;\nvar Device = loopback.models.Device;\n\n// convert from string to JSON\nmsg.payload = JSON.parse(msg.payload);\n\nDevice.registerMeasure(msg.payload, function(err, device) {\n    if (err) node.error(\"registerMeasure device error\", msg);\n    \n    node.send(msg);\n});\n    \nreturn;","outputs":1,"noerr":0,"x":266,"y":60,"wires":[["9a3f0709.65c0f8"]]},{"id":"682e54c8.97d1ac","type":"mqtt in","z":"f2181939.0de7e8","name":"glukose mqtt","topic":"glukose","broker":"4d1060c0.b2efa","x":110,"y":60,"wires":[["cbec3d13.3413c"]]}]
```

# Licenses
The source code is released under Apache 2.0.
