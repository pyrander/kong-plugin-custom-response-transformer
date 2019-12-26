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

##### you use nesting on the remove.json field too.

example:
```json
{
    "name": "kong-plugin-custom-response-transformer",
    "config": {
        "remove": {
            "json":["identity","security.user"]
        }
    }
}
```
+ this remove from the body:

This template was designed to work with the `kong-vagrant`
[development environment](https://github.com/Mashape/kong-vagrant). Please
check out that repo's `README` for usage instructions.
