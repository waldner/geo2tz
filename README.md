# Geo2Tz

[![Build Status](https://travis-ci.com/noandrea/geo2tz.svg?branch=master)](https://travis-ci.com/noandrea/geo2tz) [![GoDoc](https://godoc.org/github.com/noandrea/geo2tz?status.svg)](https://godoc.org/github.com/noandrea/geo2tz) [![Go Report Card](https://goreportcard.com/badge/github.com/noandrea/geo2tz)](https://goreportcard.com/report/github.com/noandrea/geo2tz)

A self-host-able service to get the timezone given geo-coordinates (lat/long)

It does it by exposing the library from [github.com/evanoberholster/timezoneLookup](https://github.com/evanoberholster/timezoneLookup)

Timezone data comes from [github.com/evansiroky/timezone-boundary-builder](https://github.com/evansiroky/timezone-boundary-builder) (release [2023b](https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2023b))

## Motivations

Geo-coordinates might be sensitive information to share in any context,
and I needed a self-hosted solution to ensure that coordinates were not leaked to 3rd party services.
On another side, this feature is nicely self-contained and having one service to expose it spares the effort to bundle the TZ database everywhere.

## API

the service exposes only one API:

```http
GET /tz/${LATITUDE}/${LONGITUDE}
```

that returns a JSON reply (`http/200`), for example:

```console
curl -s http://localhost:2004/tz/51.477811/0 | jq
```

```json
{
  "coords": {
    "lat": 51.47781,
    "lon": 0
  },
  "tz": "Europe/London"
}

```

or in case of errors (`http/4**`), for example:

```console
curl -v http://localhost:2004/tz/51.477811/1000 | jq
*   Trying 127.0.0.1:2004...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to localhost (127.0.0.1) port 2004 (#0)
> GET /tz/51.477811/1000 HTTP/1.1
> Host: localhost:2004
> User-Agent: curl/7.81.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 400 Bad Request
< Content-Type: application/json; charset=UTF-8
< Vary: Origin
< Date: Fri, 23 Jun 2023 19:09:29 GMT
< Content-Length: 54
<
{ [54 bytes data]
100    54  100    54    0     0  89403      0 --:--:-- --:--:-- --:--:-- 54000
* Connection #0 to host localhost left intact

```

```json
{
  "message": "lon value 1000 out of range (-180/+180)"
}
```

### Authorization

Geo2Tz supports a basic token authorization mechanism, if the configuration value for `web.auth_token_value` is a non-empty string, geo2tz will check the query parameter value to authorize incoming requests.

For example, running the service with:

```sh
docker run -p 2004:2004 -e GEO2TZ_WEB_AUTH_TOKEN_VALUE=secret noandrea/geo2tz
```

will enable authorization. With the authorization enabled, a query that does not specify the token will fail with an HTTP code 401:

```sh
> curl -sv http://localhost:2004/tz/41.902782/12.496365 | jq
```

```
*   Trying 127.0.0.1:2004...
* Connected to localhost (127.0.0.1) port 2004 (#0)
> GET /tz/41.902782/12.496365 HTTP/1.1
> Host: localhost:2004
> User-Agent: curl/7.81.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 401 Unauthorized
< Content-Type: application/json; charset=UTF-8
< Vary: Origin
< Date: Sun, 31 Jul 2022 20:06:56 GMT
< Content-Length: 27
<
{ [27 bytes data]
* Connection #0 to host localhost left intact
{
  "message": "unauthorized"
}
```

Passing the token in the query parameters will succeed instead:

```sh
> curl -s http://localhost:2004/tz/41.902782/12.496365\?t\=secret | jq
```

```json
{
  "coords": {
    "lat": 41.902782,
    "lon": 12.496365
  },
  "tz": "Europe/Rome"
}
```


## Docker

Docker image is available at [geo2tzt](https://github.com/noandrea/geo2tz/packages)

```sh
docker run -p 2004:2004 github.com/noandrea/geo2tz
```

The image is built on [scratch](https://hub.docker.com/_/scratch), the image size is ~92MB:


## Docker compose

Docker compose YAML example

```yaml
version: '3'
services:
  geo2tz:
    container_name: geo2tz
    image: github.com/noandrea/geo2tz
    ports:
    - 2004:2004
    # uncomment to enable authorization via request token
    # environment:
    # - GEO2TZ_WEB_AUTH_TOKEN_VALUE=somerandomstringhere
    # - GEO2TZ_WEB_AUTH_TOKEN_PARAM_NAME=t
    # - GEO2TZ_WEB_LISTEN_ADDRESS=":2004"

```

## K8s

Kubernetes configuration example:

```yaml
---
# Deployment
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  labels:
    app: geo2tz
  name: geo2tz
spec:
  replicas: 1
  revisionHistoryLimit: 3
  selector:
    matchLabels:
      app: geo2tz
  template:
    metadata:
      labels:
        app: geo2tz
    spec:
      containers:
      - env:
        # if this var is not empty it will enabled token authorization for requests
        #- name: GEO2TZ_WEB_AUTH_TOKEN_VALUE
        #  value: "secretsmaybebetter" # default is empty
        #- name: GEO2TZ_WEB_AUTH_TOKEN_PARAM_NAME
        #  value: "t" # default value
        #- name: GEO2TZ_WEB_LISTEN_ADDRESS
        #  value: ":2004" # default value
        image: github.com/noandrea/geo2tz:latest
        imagePullPolicy: Always
        name: geo2tz
        ports:
        - name: http
          containerPort: 2004
---
# Service
# the service for the above deployment
apiVersion: v1
kind: Service
metadata:
  name: geo2tz-service
spec:
  type: ClusterIP
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: http
  selector:
    app: geo2tz

```

## Development notes

To update the timezone database, set the version of the database in the `scripts/update-tzdata.sh` script and run:

```console
make update-tzdata
```
