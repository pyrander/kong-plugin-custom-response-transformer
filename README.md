kong-plugin-custom-response-transformer
====================

This repository contains a very simple Kong response transformer with some added functionality

##### added extract body funtion.

example:
```json
{
    "name": "kong-plugin-custom-response-transformer",
    "config": {
        "extract": {
        	"body":"meta"
        }
    }
}
```
+ this will set the meta field the new body, deleting all other siblings on the json, any "." in the value will consider nesting, in example "body":"target.meta" will search in the body a object field named target and will then set its property meta as the new body

##### you can wrap your body by registering the wrap body field.

example:
```json
{
    "name": "kong-plugin-custom-request-transformer",
    "config": {
        "wrap": {
            "body": "data"
        },
        "add": {
            "body": [
                "meta.traceId:-header.Traceid-"
            ]
        },
        "remove":{
        	"headers":["Traceid"]
        }
    }
}
```
+ this will wrap the original body inside a field called data: resulting in something like this:
```json
{
    "data": {
        "email": "test@abc.com",
        "name": "kong wrap"
    },
    "meta": {
        "traceId": "req-3640c624-7e38-4ede-9800-11ae9fd0f9f4"
    }
}
```

This template was designed to work with the `kong-vagrant`
[development environment](https://github.com/Mashape/kong-vagrant). Please
check out that repo's `README` for usage instructions.
