# Node.js proxy server to access Redis through FluidSync service

## Introduction

This proxy provides [**FluidSync**](https://github.com/nowido/FluidsyncHerokuWS) connection to Redis instance.

Prerequisites: 

- `fluidsync_ws_client` module must be installed before running proxy:

```
$npm install fluidsync_ws_client
```

- config file `redis_fluidsync_ws.config.json` must be present in work directory:

```
{
   "host" : "<hostname of Redis instance>",
   "port" : <Redis instance access port>,
   "password": "<use your secret, or remove this field>",
   "proxyName": "<something-UUID-like-unguessable-fe-954880759813FF8C>"
}
```

Clients will use `“proxyName”` to access Redis proxy; it is mandatory field. We recommend to choose a unique unguessable name. The fields `“host”`, `“port”`, and `“password”` may be omitted (defaults are `“127.0.0.1”`, `6379`, no password).

Run proxy:

```
$npm node redis_fluidsync_ws.js
```

## Clients

You can access Redis proxy from browser:

```
<script src="https://fluidsync-8f7e4.firebaseapp.com/fluidsync_ws.js"></script>
<script src="https://fluidsyncredis.firebaseapp.com/redis_client.js"></script>

...

const redis = new RedisProxy
({
    remoteNodeName: '<proxyName>'
    // see docs for other constructor parameters
});
```

You also can access Redis proxy from Node.js process:

```
$npm install fluidsync_redis_proxy

...

const RedisProxy = require('fluidsync_redis_proxy');

const redis = new RedisProxy({
    remoteNodeName: '<proxyName>'    
    // see docs for other constructor parameters
});
```

