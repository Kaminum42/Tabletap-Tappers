# 公共请求头

默认请求头略

关注部分:
```
METHOD URI HTTP/1.1
Host: <host>
User-Agent: <user-agent>
Content-Type: application/json; charset=utf-8
Content-Length: <content-length>
Accept: application/json
[Cookie: <cookie>]
```

# 公共响应头

```
HTTP/1.1 CODE MESSAGE
Content-Type: application/json; charset=utf-8
Content-Length: <content-length>
[Location: <location>]
[Set-Cookie: <cookie>]
[Cache-Control: <cache-control>]
```