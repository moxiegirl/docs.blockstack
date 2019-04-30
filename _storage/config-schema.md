---
layout: storage
permalink: /:collection/:path.html
---
# Hub configuration parameters

```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "additionalProperties": false,
    "properties": {
        "argsTransport": {
            "additionalProperties": false,
            "properties": {
                "colorize": {
                    "default": true,
                    "type": "boolean"
                },
                "handleExceptions": {
                    "default": true,
                    "type": "boolean"
                },
                "json": {
                    "default": false,
                    "type": "boolean"
                },
                "level": {
                    "default": "warn",
                    "enum": [
                        "debug",
                        "error",
                        "info",
                        "verbose",
                        "warn"
                    ],
                    "type": "string"
                },
                "timestamp": {
                    "default": true,
                    "type": "boolean"
                }
            },
            "type": "object"
        },
        "authTimestampCacheSize": {
            "default": 50000,
            "type": "integer"
        },
        "awsCredentials": {
            "additionalProperties": false,
            "description": "Required if `driver` is `aws`",
            "properties": {
                "accessKeyId": {
                    "type": "string"
                },
                "endpoint": {
                    "type": "string"
                },
                "secretAccessKey": {
                    "type": "string"
                },
                "sessionToken": {
                    "type": "string"
                }
            },
            "type": "object"
        },
        "azCredentials": {
            "additionalProperties": false,
            "description": "Required if `driver` is `azure`",
            "properties": {
                "accountKey": {
                    "type": "string"
                },
                "accountName": {
                    "type": "string"
                }
            },
            "type": "object"
        },
        "bucket": {
            "default": "hub",
            "type": "string"
        },
        "cacheControl": {
            "default": "public, max-age=1",
            "type": "string"
        },
        "diskSettings": {
            "additionalProperties": false,
            "description": "Required if `driver` is `disk`",
            "properties": {
                "storageRootDirectory": {
                    "type": "string"
                }
            },
            "type": "object"
        },
        "driver": {
            "enum": [
                "aws",
                "azure",
                "disk",
                "google-cloud"
            ],
            "type": "string"
        },
        "gcCredentials": {
            "additionalProperties": false,
            "description": "Required if `driver` is `google-cloud`",
            "properties": {
                "credentials": {
                    "additionalProperties": false,
                    "properties": {
                        "client_email": {
                            "type": "string"
                        },
                        "private_key": {
                            "type": "string"
                        }
                    },
                    "type": "object"
                },
                "email": {
                    "type": "string"
                },
                "keyFilename": {
                    "type": "string"
                },
                "projectId": {
                    "type": "string"
                }
            },
            "type": "object"
        },
        "pageSize": {
            "default": 100,
            "maximum": 4096,
            "minimum": 1,
            "type": "integer"
        },
        "port": {
            "default": 3000,
            "maximum": 65535,
            "minimum": 0,
            "type": "integer"
        },
        "proofsConfig": {
            "additionalProperties": false,
            "properties": {
                "proofsRequired": {
                    "default": 0,
                    "type": "integer"
                }
            },
            "type": "object"
        },
        "readURL": {
            "type": "string"
        },
        "requireCorrectHubUrl": {
            "default": false,
            "type": "boolean"
        },
        "serverName": {
            "default": "gaia-0",
            "description": "Domain name used for auth/signing challenges. \nIf `requireCorrectHubUrl` is true then this must match the hub url in an auth payload.",
            "type": "string"
        },
        "validHubUrls": {
            "description": "If `requireCorrectHubUrl` is true then the hub specified in an auth payload can also be\ncontained within in array.",
            "items": {
                "type": "string"
            },
            "type": "array"
        },
        "whitelist": {
            "description": "List of ID addresses allowed to use this hub. Specifying this makes the hub private \nand only accessible to the specified addresses. Leaving this unspecified makes the hub \npublicly usable by any ID.",
            "items": {
                "type": "string"
            },
            "type": "array"
        }
    },
    "required": [
        "driver",
        "port"
    ],
    "type": "object"
}
```
