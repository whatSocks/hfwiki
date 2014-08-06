In order to get basic security on your domain webpage (http://yourdomain:40100). You need to create or edit the config.json in your domain's resource folder.

This config is written in [JSON format](http://en.wikipedia.org/wiki/JSON).

The basic-auth key holds the basic authentication credentials. Every credential exists out of an object with the username as key and the contains a password key with the desired password as value.

Here is an example:
```json
{
    "basic-auth": {
        "USERNAME HERE": {
            "password": "PASSWORD HERE"
        },
        "USERNAME2 HERE": {
            "password": "PASSWORD2 HERE"
        }
    }
}
```

> Note: be sure to use comma's in the right positions.