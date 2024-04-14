# 发送私信

## 说明

发送私信


## 要求

登录认证: 需要

身份 / 权限: 本人

## 请求方法

`POST`

## 路径

`/api/v1/messages`

## 请求头

参考公共请求头

## 查询参数

无

## 请求体

请求体类型: `application/json`

### 字段说明

- `to_user`
    - 数据类型: `number`
    - 描述: 接收者ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `20000`

- `content`
    - 数据类型: `string`
    - 描述: 消息内容
    - 约束: 长度 1-2048, Unicode 字符
    - 是否必须: 是
    - 示例: `Hello, world!`

- `details`
    - 数据类型: `Object`
    - 描述: 其他详细信息
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`


## 请求示例

```
POST /api/v1/messages HTTP/1.1
...

{
    "to_user": 20000,
    "content": "Hello, world!",
    "details": {"key": "value"}
}
```

## 响应头

### 响应状态码

- `201`: 发送成功

- `400`: 请求格式不正确

- `401`: 需要进行登录

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
HTTP/1.1 201 Created
...

{
    "code": 201,
    "message": "Created",
    "body": {}
}
```