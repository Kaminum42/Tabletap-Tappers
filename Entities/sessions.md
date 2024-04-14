## 字段

- `session_id`
    - 数据类型: `string`
    - 描述: 会话 ID
    - 约束: Unicode 字符串
    - 是否必须: 是
    - 示例: `s%3AFq43f3qIs5T57D27pPJtI3QYzS02dI`

- `user_id`
    - 数据类型: `number`
    - 描述: 用户 ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `10000`

- `permission_level`
    - 数据类型: `number`
    - 描述: 权限等级, 0 ~ 99 system, 100 ~ 199 admin, 200 ~ 299 server, 300 ~ 399 user, 400 ~ 499 guest, 其余保留
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `0`

- `create_time`
    - 数据类型: `number`
    - 描述: 会话创建时间
    - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
    - 是否必须: 否
    - 示例: `1704038400000`

- `expire_time`
    - 数据类型: `number`
    - 描述: 会话过期时间
    - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
    - 是否必须: 否
    - 示例: `1704038400000`

- `details`
    - 数据类型: `string`
    - 描述: 其他详细信息
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`