# Report Error

`POST https://app.errordeck.com/api/:project_id/store`

This endpoint is used to report an error to Errordeck.

## Request

### Headers

| Name | Type | Description |
| ---- | ---- | ----------- |
| `Content-Type` | `application/json` | The content type of the request. |
| `Authorization` | `Bearer <token>` | The authorization token. |

### Body

```json
{
  "event_id": "7b48f3ee3fec4121b4567ea76c5c65be",
  "timestamp": 1677934935,
  "platform": "ruby",
  "level": "error",
  "logger": "ruby",
  "transaction": null,
  "server_name": null,
  "release": "0.0.0",
  "dist": "0.0.0",
  "environment": "development",
  "message": "test",
  "modules": null,
  "extra": null,
  "exceptions": null,
  "contexts": null,
  "request": null,
  "sdk": {
    "name": "errordeck-ruby",
    "version": "0.1.0"
  },
  "user": null
}
```

This is the least amount of data that you need to send to Errordeck.

#### Body parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `event_id` | `String` | The id of the error. |
| `timestamp` | `Int32` | The timestamp of the error. |
| `platform` | `String` | The platform of the error, example `ruby` or `javascript`. |
| `level` | `String` | The level of the error. |
| `logger` | `String` | The logger of the error. |
| `transaction` | `String` | The transaction or culprit class of the error. |
| `server_name` | `String` | The server name where the error happened. |
| `release` | `String` | The release of the error. |
| `dist` | `String` | The distribution name of the error. |
| `environment` | `String` | The environment of the application. |
| `message` | `String` | The message of the error. |
| `modules` | `Hash(String, String)?` | The modules of the error. |
| `extra` | `Hash(String, String)?` | The extra data of the error. |
| `exceptions` | `Array(Exception)?` | The exceptions of the error. |
| `contexts` | `Hash(String, Context)?` | The contexts of the error. |
| `request` | `Request?` | The request of the error. |
| `sdk` | `Sdk` | The sdk of the error. |
| `user` | `User?` | The user of the error. |

### Exception

Exception is the most important part of the error. It contains the stacktrace and the message of the error.

```json
{
  "type": "ZeroDivisionError",
  "value": "divided by 0",
  "module": null,
  "thread_id": 0,
  "stacktrace": [
    {
      "filename": "test.rb",
      "function": "test",
      "lineno": 2,
      "colno": 0,
      "in_app": true
    },
    {
      "filename": "test.rb",
      "function": "main",
      "lineno": 5,
      "colno": 0,
      "in_app": true
    }
  ]
}
```

#### Body parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `type` | `String` | The type of the exception. |
| `value` | `String` | The message of the exception. |
| `module` | `String` | The module of the exception. |
| `thread_id` | `Int32` | The thread id of the exception. |
| `stacktrace` | `Array(Stacktrace)` | The stacktrace of the exception. |

### Stacktrace

Stacktrace is the stacktrace of the exception. It contains the filename, function, line number, column number and if it is in the application.

```json
{
  "filename": "test.rb",
  "function": "test",
  "lineno": 2,
  "colno": 0,
  "in_app": true
}
```

#### Body parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `filename` | `String` | The filename of the stacktrace. |
| `function` | `String` | The function of the stacktrace. |
| `lineno` | `Int32` | The line number of the stacktrace. |
| `colno` | `Int32` | The column number of the stacktrace. |
| `in_app` | `Bool` | If the stacktrace is in the application. |

### Request

```json
{
  "url": "http://localhost:3000/",
  "method": "GET",
  "headers": {
    "Accept": "*/*",
    "Accept-Encoding": "gzip;q=1.0,deflate;q=0.6,identity;q=0.3",
    "Accept-Language": "en-US;q=1.0,en;q=0.9",
    "Connection": "close",
    "Host": "localhost:3000",
    "User-Agent": "HTTPie/0.9.9"
  },
  "env": {
    "GATEWAY_INTERFACE": "CGI/1.2",
    "HTTP_ACCEPT": "*/*",
    "HTTP_ACCEPT_ENCODING": "gzip;q=1.0,deflate;q=0.6,identity;q=0.3",
    "HTTP_ACCEPT_LANGUAGE": "en-US;q=1.0,en;q=0.9",
    "HTTP_CONNECTION": "close",
    "HTTP_HOST": "localhost:3000",
    "HTTP_USER_AGENT": "HTTPie/0.9.9",
    "PATH_INFO": "/",
    "QUERY_STRING": "",
    "REMOTE_ADDR": ""
  },
  "data": null
}
```

#### Body parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `url` | `String` | The url of the request. |
| `method` | `String` | The method of the request. |
| `headers` | `Hash(String, String)` | The headers of the request. |
| `env` | `Hash(String, String)` | The env of the request. |
| `data` | `Hash(String, String)?` | The data of the request. |

### Sdk

SDK is the sdk that is sending the error. It contains the name and the version of the sdk.

```json
{
  "name": "errordeck-ruby",
  "version": "0.1.0"
}
```

#### Body parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `name` | `String` | The name of the sdk. |
| `version` | `String` | The version of the sdk. |


### User

User is optional and is flexible. You can send any data you want. But we recommend to not send any user data here, except for internal id. We only use this data for counting unique users. We create an hash and throw away the data.

```json
{
  "id": "1"
}
```

#### Body parameters

| Name | Type | Description | 
| ---- | ---- | ----------- |
| `id` | `String` | The id of the user. |
