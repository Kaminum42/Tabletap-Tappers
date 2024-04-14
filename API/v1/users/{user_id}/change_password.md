# 修改密码

## 说明

修改密码

## 要求

登录认证: 需要

身份 / 权限: 用户本人或管理员

## 请求方法

`POST`

## 路径

`/api/v1/users/{user_id}/change_password`

- `user_id`
    - 数据类型: `number`
    - 描述: 用户ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `10000`

## 请求头

参考公共请求头

## 查询参数

## 请求体

请求体类型: `application/json`

### 字段说明

- `original_password`
    - 数据类型: `string`
    - 描述: 用户的原密码, 使用 BCrypt 算法加密再传输, 盐通过 API 获取, 可调用 `bcryptjs` 库
    - 约束: 合法的 BCrypt 密文
    - 是否必须: 非管理员时必须
    - 示例: `$2b$10$qc6teflL2F2SRMvEkG48te2JQSzju67UL.JGsp.pzc/cWvfEnxI9y`

- `new_password`
    - 数据类型: `string`
    - 描述: 用户的新密码, 使用 BCrypt 算法加密再传输, 盐选取 `轮数 = 10` 随机生成, 可调用 `bcryptjs` 库
    - 约束: 合法的 BCrypt 密文
    - 是否必须: 是
    - 示例: `$2b$10$BO2X.9KieFtDIdspeoz3SupgZQUYhIQVl90x9LRgtA.ypR9gDsgdK`

## 请求示例

```
POST /api/v1/users/{user_id}/change_password HTTP/1.1
...

{
    "original_password": "$2b$10$qc6teflL2F2SRMvEkG48te2JQSzju67UL.JGsp.pzc/cWvfEnxI9y",
    "new_password": "$2b$10$BO2X.9KieFtDIdspeoz3SupgZQUYhIQVl90x9LRgtA.ypR9gDsgdK"
}
```


## 响应头

### 响应状态码

- `200`: 修改成功

- `400`: 请求格式不正确

- `401`: 需要进行登录

- `403`: 没有足够的权限

- `404`: 找不到该用户

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

无

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