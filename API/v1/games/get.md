# 查询游戏表

## 说明

查询游戏表

## 要求

登录认证: 不需要

身份 / 权限: 部分字段需要管理员

## 请求方法

`GET`

## 路径

`/api/v1/games`

## 请求头

参考公共请求头

## 查询参数

- `page`
    - 数据类型: `number`
    - 描述: 返回该搜索的第几页, 默认为 `1`
    - 约束: 正整数
    - 是否必须: 否
    - 示例: `1`

- `page_size`
    - 数据类型: `number`
    - 描述: 结果保留最多多少条数据, 默认为 `10`
    - 约束: 正整数, 1 ~ 50
    - 是否必须: 否
    - 示例: `1`

- `sort`
    - 数据类型: `string`
    - 描述: 按照什么字段进行 升/降序 排序, 默认升序, 如有嵌套字段用 `.` 号连接, 多个字段排序用 `,` 隔开
    - 约束: 至少一个字段
    - 是否必须: 否
    - 示例: `game-name|desc`

- `keyword`
    - 数据类型: `string`
    - 描述: 用于模糊匹配 game_name 或 description
    - 约束: Unicode 字符串, 不超过 32 字符
    - 是否必须: 否
    - 示例: `富翁`

## 请求体

请求体类型: 无

### 字段说明

[无]

## 请求示例

```
GET /api/v1/games?page=1&page_size=10&sort=game_id|desc&keyword=%E5%AF%8C%E7%BF%81 HTTP/1.1
...
```

## 响应头

### 响应状态码

- `200`: 查询成功

- `400`: 请求格式不正确

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

无

## 响应体

响应体类型: `application/json`

### 字段说明

- `results`
    - 数据类型: `Array`
    - 描述: 搜索结果
    - 约束: --
    - 是否必须: 是
    - 示例: --

    - `game_id`
        - 数据类型: `number`
        - 描述: 游戏 ID
        - 约束: 整数, 0 ~ 2^32-1
        - 是否必须: 是
        - 示例: `1`

    - `game_name`
        - 数据类型: `string`
        - 描述: 游戏名称
        - 约束: 长度 1-32, Unicode 字符
        - 是否必须: 是
        - 示例: `大富翁`

    - `on_shelve`
        - 数据类型: `boolean`
        - 描述: 游戏上架状态, `true` 表示上架, `false` 表示下架
        - 约束: `true` 或 `false`
        - 是否必须: 是
        - 示例: `true`

    - `create_date`
        - 数据类型: `number`
        - 描述: 游戏创建日期
        - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
        - 是否必须: 否
        - 示例: `1704038400000`

    - `description`
        - 数据类型: `string`
        - 描述: 游戏描述
        - 约束: 长度 1-2048, Unicode 字符
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
        - 是否必须: 否(仅管理员可见)
        - 示例: `monopoly:latest`

    - `server_config`
        - 数据类型: `string`
        - 描述: 游戏服务器镜像配置文件
        - 约束: 配置文件的路径
        - 是否必须: 否(仅管理员可见)
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

## 响应示例

```
HTTP/1.1 200 OK
...

{
    "code": 200,
    "message": "OK",
    "body": [
        {
            "game_id": 1,
            "game_name": "大富翁",
            "on_shelve": true,
            "create_date": 1704038400000,
            "description": "大富翁，又名地产大亨，是一种多人策略图版游戏。",
            "cover_url": "https://124.71.19.191/res/uploads/cover.jpg",
            "icon_url": "https://124.71.19.191/res/uploads/icon.png",
            "client_resources": "https://124.71.19.191/res/games/{game_name}/index.html",
            "client_config": {"key": "value"},
            "details": {"key": "value"}
        },
        {
            ...
        }
    ]
}
```