# 修改公告

## 说明

修改公告

## 要求

登录认证: 需要

身份 / 权限: 需要

## 请求方法

`PUT`

## 路径

`/api/v1/announcements/{announcements_id}`

- `announcement_id`
    - 数据类型: `number`
    - 描述: 公告 ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `1`

## 请求头

参考公共请求头

## 查询参数

无

## 请求体

请求体类型: `application/json`

### 字段说明

- `title`
    - 数据类型: `string`
    - 描述: 公告标题
    - 约束: 长度 1-64, Unicode 字符
    - 是否必须: 是
    - 示例: `测试标题`

- `content`
    - 数据类型: `string`
    - 描述: 公告内容
    - 约束: 长度 1-2048, Unicode 字符
    - 是否必须: 是
    - 示例: `测试内容`

- `details`
    - 数据类型: `Object`
    - 描述: 其他详细信息
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`

## 请求示例

```
PUT /api/v1/announcements/{announcements_id} HTTP/1.1
...

{
    "title": "测试标题",
    "content": "测试内容"
}
```

## 响应头

### 响应状态码

- `200`: 修改成功

- `400`: 请求格式不正确

- `401`: 需要进行登录

- `403`: 没有足够的权限

- `404`: 找不到该公告

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