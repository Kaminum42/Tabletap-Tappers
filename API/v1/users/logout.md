# 登出用户

## 说明

登出用户

## 要求

登录认证: 需要

身份 / 权限: 用户本人或管理员

## 请求方法

`POST`

## 路径

`/api/v1/users/{user_id}/logout`

- `user_id`
    - 数据类型: `number`
    - 描述: 用户ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `10000`

## 请求头

参考公共请求头

## 查询参数

无

## 请求体

请求体类型: 无

### 字段说明

无

## 请求示例

```
POST /api/v1/users/{user_id}/logout HTTP/1.1
...
```

## 响应头

### 响应状态码

- `200`: 登出成功

- `400`: 请求格式不正确

- `401`: 需要先登录

- `403`: 没有权限登出

- `404`: 找不到该用户

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

- `Set-Cookie`
    - 数据类型: `string`
    - 描述: 更改 Cookie, 销毁用户会话
    - 约束: 合法的 Cookie 字符串
    - 是否必须: 是
    - 示例: `sessionid=...; ...`

## 响应体

响应体类型: `application/json`

### 字段说明

无

## 响应示例

```
HTTP/1.1 200 OK
...

{
    "code": 200,
    "message": "OK",
    "body": {}
}
```