# 上架游戏

## 说明

上架游戏

## 要求

登录认证: 需要

身份 / 权限: 管理员

## 请求方法

`POST`

## 路径

`/api/v1/games/{game_id}/open`

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

请求体类型: 无

### 字段说明

无

## 请求示例

```
POST /api/v1/games/1/open HTTP/1.1
...
```

## 响应头

### 响应状态码

- `202`: 正在上架游戏

- `400`: 请求格式不正确

- `401`: 需要进行登录

- `403`: 没有足够的权限

- `404`: 找不到该游戏

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
HTTP/1.1 202 Accepted
...

{
    "code": 202,
    "message": "Accepted",
    "body": {}
}
```