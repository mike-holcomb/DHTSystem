# JSONRouter
A simple server that responds to JSON requests. It listens for requests on port 9000 of the format:

 * 	method - Method name

 * 	to - Name of intended server

 * 	from - Name of client

 * 	params - JSON object containing parameters for method
 
It returns a response of the form

 * 	response - Always OK, probably should actually do something with request first 

 * 	to - Client name 

 *	from - Name of intended server.

## Example
 
 In one terminal session run:

```
java -jar ./build/JSONRouter.jar
 
==== Base JSON Server =====

Listening on port: 9000
```
 
 In a second terminal session run:
 ```
 nc 127.0.0.1 9000
{ "method": "write", "to":"A", "from":"B", "params": { "a":1, "b":2 } } 
```

You should the response in the server window of:
```
Opening request router...
Request received...
{ "method": "write", "to":"A", "from":"B", "params": { "a":1, "b":2 } }
A received command to write from B with parameters {"a":1,"b":2}
WRITE: Params provided were: {"a":1,"b":2}
```

Hit CTRL+C to end the client session and separately to end the server session.