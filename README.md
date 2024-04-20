## Control 4 driver - szWebControl
A simple http driver that can change a system variable value and record the history of changes. The driver can be used to integrate Control4 with other home automation systems..

## Version history
* Version 5. Initial revision.

## Requirements
Tested on OS version 3.3.0 and 3.3.2.

## How to use:
1. Install the driver.
2. Change the listening port if needed. The default port is 40088.
3. The driver is now listening for HTTP requests. 
4. Use address found at "Server Url" property to send POST JSON requests to the driver and receive JSON responses.

## JSON requests samples
Request sample 1:
```
{
	"command":"setSystemVariable", 
	"name":"TEST_VARIABLE_1", 
	"value":"some-value"
}
```

Request sample 2:
```
[
{
	"command":"setSystemVariable", 
	"name":"TEST_VARIABLE_1", 
	"value":"parameterized value: {1}, {2}",
	"valueParams" : {
		"1":"param1",
		"2":"param2"
	}
},
{
	"command":"setSystemVariable", 
	"name":"TEST_VARIABLE_2", 
	"value":"CURRENT TIME: {time}"
},
{
	"command":"setSystemVariable", 
	"name":"TEST_VARIABLE_3", 
	"value":"{date} {time}"
}
]
```

Response sample 1:
```
{
	"result": true
}
```

Response sample 2:
```
{
	"result": false,
	"error": "Command 'setSystemVariable' failed: Unknown system variable 'TEST_VARIABLE_4'"
}
```

Response sample 3:
```
{
	"result": false,
	"error": "Command or array of commands is required"
}
```

Response sample 4:
```
{
	"result": false,
	"error": "Bad variable value"
}
```




