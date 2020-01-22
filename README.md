kong-plugin-custom-response-transformer
====================

This repository contains a very simple Kong response transformer with some added functionality

### added extract body funtion.

example:
```json
{
    "name": "kong-plugin-custom-response-transformer",
    "config": {
        "extract": {
        	"body":["meta","error"]
        }
    }
}
```
+ this will set the meta field as the new body, if meta is not present it will set error as the new body, if meta is present then his error field will be set as the new body (equivalent to set ["meta.error"]). If meta does not have an error field, meta will be returned as the body. 

+ this operation will delete all other siblings on the json, any "." in the value will be considered as nesting. For example "body":["target.meta"] will search in the body a object field named target and then set it's property meta as the new body

### nesting can be used on the remove.json field too.

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
+ this will remove from the body the field identity at root and the field user inside security

This template was designed to work with the `kong-vagrant`
[development environment](https://github.com/Mashape/kong-vagrant). Please
check out that repo's `README` for usage instructions.
