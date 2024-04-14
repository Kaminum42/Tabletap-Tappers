# 注册用户

## 说明

注册用户

## 要求

登录认证: 不需要

身份 / 权限: 不需要

## 请求方法

`POST`

## 路径

`/api/v1/users`

## 请求头

参考公共请求头

## 查询参数

无

## 请求体

请求体类型: `application/json`

### 字段说明
 
- `username`
    - 数据类型: `string`
    - 描述: 用户名, 唯一且不可更改
    - 约束: 长度 4-32 , 允许字符为大小写英文, 数字, 下划线 `_` 和连字符 `-`
    - 是否必须: 是
    - 示例: `zhangsan`

- `password`
    - 数据类型: `string`
    - 描述: 使用 BCrypt 算法对 password 加密再传输, 盐选取 `轮数 = 10` 随机生成, 可调用 `bcryptjs` 库, 不可见
    - 约束: 合法的 BCrypt 密文
    - 是否必须: 是
    - 示例: `$2b$10$qc6teflL2F2SRMvEkG48te2JQSzju67UL.JGsp.pzc/cWvfEnxI9y`

- `nickname`
    - 数据类型: `string`
    - 描述: 昵称, `profile_visibility` 为 `false` 时不可见
    - 约束: 长度 4-32, Unicode 字符
    - 是否必须: 否
    - 示例: `张三`

- `email`
    - 数据类型: `string`
    - 描述: 电子邮箱地址, `profile_visibility` 为 `false` 时不可见
    - 约束: 合法的 Email 地址
    - 是否必须: 否
    - 示例: `123456@qq.com`

- `gender`
    - 数据类型: `string`
    - 描述: 性别, `profile_visibility` 为 `false` 时不可见
    - 约束: `男` 或 `女` 或 `保密`
    - 是否必须: 否
    - 示例: `男`

- `birthday`
    - 数据类型: `number`
    - 描述: 生日, `profile_visibility` 为 `false` 时不可见
    - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
    - 是否必须: 否

- `phone`
    - 数据类型: `string`
    - 描述: 手机号码, `profile_visibility` 为 `false` 时不可见
    - 约束: 合法的手机号码
    - 是否必须: 否
    - 示例: `13912345678`

- `address`
    - 数据类型: `string`
    - 描述: 地址, `profile_visibility` 为 `false` 时不可见
    - 约束: 长度 4-64, Unicode 字符
    - 是否必须: 否
    - 示例: `上海市浦东新区`

- `profile_visibility`
    - 数据类型: `boolean`
    - 描述: 用户档案可见性, `true` 为公开, `false` 为不公开, 默认为公开
    - 约束: `true` 或者 `false`
    - 是否必须: 否
    - 示例: `true`

- `details`
    - 数据类型: `Object`
    - 描述: 其他详细信息, `profile_visibility` 为 `false` 时不可见
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`

## 请求示例

```
POST /api/v1/users HTTP/1.1
...

{
    "username": "zhangsan",
    "password": "$2b$10$qc6teflL2F2SRMvEkG48te2JQSzju67UL.JGsp.pzc/cWvfEnxI9y",
    "nickname": "张三"
}
```

## 响应头

### 响应状态码

- `201`: 注册成功

- `400`: 请求格式不正确

- `409`: 该用户已经存在

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
HTTP/1.1 201 Created
...
Location: /api/users/{user_id}
Set-Cookie: sessionid=<session_id>; ...

{
    "code": 201,
    "message": "Created",
    "body": {}
}
```