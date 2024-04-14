# 修改游戏信息

## 说明

修改游戏信息

## 要求

登录认证: 需要

身份 / 权限: 管理员

## 请求方法

`PUT`

## 路径

`/api/v1/games/{game_id}`

- `game_id`
    - 数据类型: `number`
    - 描述: 游戏 ID
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

[无]

或者

- `game_name`
    - 数据类型: `string`
    - 描述: 游戏名称
    - 约束: 长度 1-32, Unicode 字符
    - 是否必须: 否
    - 示例: `大富翁`

- `create_date`
    - 数据类型: `number`
    - 描述: 游戏创建日期
    - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
    - 是否必须: 否
    - 示例: `1704038400000`

- `description`
    - 数据类型: `string`
    - 描述: 游戏描述
    - 约束: 长度 0-2048, Unicode 字符
    - 是否必须: 否
    - 示例: `大富翁，又名地产大亨，是一种多人策略图版游戏。`

- `cover_url`
    - 数据类型: `string`
    - 描述: 封面 URL
    - 约束: URL 格式
    - 是否必须: 否
    - 示例: `https://124.71.19.191/res/uploads/cover.jpg`

- `icon_url`
    - 数据类型: `string`
    - 描述: 图标 URL
    - 约束: URL 格式
    - 是否必须: 否
    - 示例: `https://124.71.19.191/res/uploads/icon.png`

- `server_image`
    - 数据类型: `string`
    - 描述: 游戏服务器镜像
    - 约束: 游戏镜像的镜像名
    - 是否必须: 否
    - 示例: `monopoly:latest`

- `server_config`
    - 数据类型: `string`
    - 描述: 游戏服务器镜像配置文件
    - 约束: 配置文件的路径
    - 是否必须: 否
    - 示例: `/app/games/{game_name}/docker-compose.json`

- `client_resources`
    - 数据类型: `string`
    - 描述: 前端资源
    - 约束: 前端资源的 URL 链接
    - 是否必须: 否
    - 示例: `https://124.71.19.191/res/games/{game_name}/index.html`

- `client_config`
    - 数据类型: `string`
    - 描述: 前端配置
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`

- `details`
    - 数据类型: `Object`
    - 描述: 其他详细信息
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`


## 请求示例

```
PUT /api/v1/games/{game_id} HTTP/1.1
...

{
    "game_name": "大富翁",
    "description": "大富翁，又名地产大亨，是一种多人策略图版游戏。"
}
```

## 响应头

### 响应状态码

- `200`: 修改成功

- `400`: 请求格式不正确

- `401`: 需要进行登录

- `403`: 没有足够的权限

- `404`: 找不到该游戏

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

## 响应体

响应体类型: `application/json`

### 字段说明

无

## 响应示例

```
HTTP/1.1 200 OK
...
[响应头字段]

{
    "code": 200,
    "message": "OK",
    "body": {}
}
```