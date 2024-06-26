# 查询游戏排行榜

## 说明

查询游戏排行榜

## 要求

登录认证: 不需要

身份 / 权限: 不需要

## 请求方法

`GET`

## 路径

`/api/v1/rankings`

## 请求头

参考公共请求头

## 查询参数

- `game`
    - 数据类型: `number`
    - 描述: 游戏ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 否
    - 示例: `1`

- `user`
    - 数据类型: `number`
    - 描述: 用户 ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 否
    - 示例: `10000`

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
    - 示例: `game_id|desc,total_score|desc,user_id|desc`

## 请求体

请求体类型: 无

### 字段说明

无

## 请求示例

```
GET /api/v1/rankings?page=1&page_size=10&sort=game_id|desc,total_score|desc,user_id|desc HTTP/1.1
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
        - 描述: 关联的游戏 ID
        - 约束: 整数, 0 ~ 2^32-1
        - 是否必须: 是
        - 示例: `1`

    - `user_id`
        - 数据类型: `number`
        - 描述: 关联的用户 ID
        - 约束: 整数, 0 ~ 2^32-1
        - 是否必须: 是
        - 示例: `10000`

    - `count`
        - 数据类型: `number`
        - 描述: 总局数
        - 约束: 整数, 0 ~ 2^32-1
        - 是否必须: 是
        - 示例: `100`

    - `max_score`
        - 数据类型: `number`
        - 描述: 历史最高得分
        - 约束: 整数, 0 ~ 2^32-1
        - 是否必须: 是
        - 示例: `10`

    - `total_score`
        - 数据类型: `number`
        - 描述: 总分
        - 约束: 整数, 0 ~ 2^32-1
        - 是否必须: 是
        - 示例: `1000`

    - `update_time`
        - 数据类型: `number`
        - 描述: 最后一次更新时间
        - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
        - 是否必须: 否
        - 示例: `1704038400000`

    - `details`
        - 数据类型: `Object`
        - 描述: 其他信息
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
            "user_id": 10000,
            "count": 100,
            "max_score": 10,
            "total_score": 1000,
            "update_time": 1704038400000,
            "details": {
                "key": "value"
            },
            {
                ...
            }
        }
    ]
}
```