# 登录用户

## 说明

登录用户

## 要求

登录认证: 不需要

身份 / 权限: 不需要

## 请求方法

`POST`

## 路径

`/api/v1/users/login`

## 请求头

参考公共请求头

## 查询参数

无

## 请求体

请求体类型: `application/json`

### 字段说明

- `method`
    - 数据类型: `string`
    - 描述: 登陆方法, 用户 ID / 用户名 / 邮箱, 未被选中的字段将被忽略
    - 约束: 必须为 `user_id`, `username`, `email` 中的一项
    - 是否必须: 是
    - 示例: `username`

- `user_id`
    - 数据类型: `number`
    - 描述: 用户 ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: `method = user_id` 时必须
    - 示例: `10000`

- `username`
    - 数据类型: `string`
    - 描述: 用户名, 唯一且不可更改
    - 约束: 长度 4-32 , 允许字符为大小写英文, 数字, 下划线 `_` 和连字符 `-`
    - 是否必须: `method = username` 时必须
    - 示例: `zhangsan`

- `email`
    - 数据类型: `string`
    - 描述: 电子邮箱地址
    - 约束: 合法的 Email 地址
    - 是否必须: `method = email` 时必须
    - 示例: `123456@qq.com`

- `password`
    - 数据类型: `string`
    - 描述: 使用 BCrypt 算法对 password 加密再传输, 盐通过 API 获取, 可调用 `bcryptjs` 库
    - 约束: 合法的 BCrypt 密文
    - 是否必须: 是
    - 示例: `$2b$10$qc6teflL2F2SRMvEkG48te2JQSzju67UL.JGsp.pzc/cWvfEnxI9y`

## 请求示例

```
POST /api/v1/users/login HTTP/1.1
...

{
    "method": "username",
    "username": "zhangsan",
    "password": "$2b$10$qc6teflL2F2SRMvEkG48te2JQSzju67UL.JGsp.pzc/cWvfEnxI9y"
}
```

## 响应头

### 响应状态码

- `200`: 登录成功

- `400`: 请求格式不正确

- `401`: 用户名或密码错误

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

- `Location`
    - 数据类型: `string`
    - 描述: 用户空间的 URI
    - 约束: 合法的 URI
    - 是否必须: 是
    - 示例: `/api/users/10000`

- `Set-Cookie`
    - 数据类型: `string`
    - 描述: 添加 Cookie, 用户会话管理等等
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
Location: /api/users/{user_id}
Set-Cookie: sessionid=<session_id>; ...

{
    "code": 200,
    "message": "OK",
    "body": {}
}
```