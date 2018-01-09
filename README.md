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
