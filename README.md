# node-soap-java

### create SpringBoot Project 
[Spring Boot](https://start.spring.io/) initializr is good starting point for project setup

### import WSDL to project 
```bash
cd <project/src/main/java>
wsimport -extension -keep http://www.gcomputer.net/webservices/dilbert.asmx?WSDL
```

### Write Endpoints from imported WSDL
find all supported endpoints from WSDL document
this has to be done manually

### start java soap server
* `./mvnw install`
* `./mvnw spring-boot:run`

### access soap server from node js

```javascript
var request = require("request");

var daily_options = { method: 'POST',
  url: 'http://localhost:8080/daily',
  headers: 
   { 'cache-control': 'no-cache',
     'content-type': 'application/json' },
  body: { adate: 1473631656137 },
  json: true };

request(daily_options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});



var today_options = { method: 'GET',
  url: 'http://localhost:8080/today',
  headers: 
   {'cache-control': 'no-cache' } };

request(today_options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```
