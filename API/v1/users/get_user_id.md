# 获取用户 ID

## 说明

根据用户名 / 邮箱获取 ID

## 要求

登录认证: 不需要

身份 / 权限: 不需要

## 请求方法

`POST`

## 路径

`/api/v1/users/get_user_id`

## 请求头

参考公共请求头

## 查询参数

无

## 请求体

请求体类型: `application/json`

### 字段说明

- `method`
    - 数据类型: `string`
    - 描述: 查询方法, 用户名 / 邮箱, 未被选中的字段将被忽略
    - 约束: 必须为 `username`, `email` 中的一项
    - 是否必须: 是
    - 示例: `username`

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

## 请求示例

```
POST /api/v1/users/get_user_id HTTP/1.1
...

{
    "method": "username",
    "username": "zhangsan"
}
```

## 响应头

### 响应状态码

- `200`: 查找成功

- `400`: 请求格式不正确

- `404`: 该用户不存在

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

无

## 响应体

响应体类型: `application/json`

### 字段说明

- `user_id`
    - 数据类型: `number`
    - 描述: 用户 ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `10000`

## 响应示例

```
HTTP/1.1 200 OK
...

{
    "code": 200,
    "message": "OK",
    "body": {
        "user_id": 10000
    }
}
```