# [API名]

## 说明

[API说明]

## 要求

登录认证: [不需要|需要|...]

身份 / 权限: [不需要|需要|...]

[...]

## 请求方法

[`GET`|`POST`|`PUT`|`DELETE`]

## 路径

[`/api/v1/...`]

- `字段`
    - 数据类型: [`string`|`number`|`boolean`|...]
    - 描述: [字段描述]
    - 约束: [数据约束]
    - 是否必须: [是|否|...时必须|...]
    - 示例: [`字段示例`]

## 请求头

参考公共请求头

- `字段`
    - 数据类型: [`string`|`number`|`boolean`|...]
    - 描述: [字段描述]
    - 约束: [数据约束]
    - 是否必须: [是|否|...时必须|...]
    - 示例: [`字段示例`]

## 查询参数

[无]

或者

- `字段`
    - 数据类型: [`string`|`number`|`boolean`|...]
    - 描述: [字段描述]
    - 约束: [数据约束]
    - 是否必须: [是|否|...时必须|...]
    - 示例: [`字段示例`]

## 请求体

请求体类型: [无|`application/json`]

### 字段说明

[无]

或者

- `字段`
    - 数据类型: [`string`|`number`|`boolean`|...]
    - 描述: [字段描述]
    - 约束: [数据约束]
    - 是否必须: [是|否|...时必须|...]
    - 示例: [`字段示例`]

## 请求示例

```
[METHOD] [URI] HTTP/1.1
...
[请求头字段]
```

或者

```
[METHOD] [URI] HTTP/1.1
...
[请求头字段]

{
    "key": "value"
}
```

## 响应头

### 响应状态码

- `200`: [...]成功

- `201`: [...]创建成功

- `202`: 请求已成功提交

- `204`: 请求成功, 但没有返回内容

- `400`: 请求格式不正确

- `401`: 需要进行登录

- `403`: 没有足够的权限

- `404`: 找不到[...]

- `409`: [...]已存在 / 请求出现冲突

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

[无]

或者

- `字段`
    - 数据类型: [`string`|`number`|`boolean`|...]
    - 描述: [字段描述]
    - 约束: [数据约束]
    - 是否必须: [是|否|...时必须|...]
    - 示例: [`字段示例`]

## 响应体

响应体类型: `application/json`

### 字段说明

[无]

或者

- `字段`
    - 数据类型: [`string`|`number`|`boolean`|...]
    - 描述: [字段描述]
    - 约束: [数据约束]
    - 是否必须: [是|否|...时必须|...]
    - 示例: [`字段示例`]

## 响应示例

```
HTTP/1.1 [状态码] [状态字符串]
...
[响应头字段]

{
    "code": [状态码],
    "message": [状态字符串],
    "body": {
        "key": "value"
    }
}
```