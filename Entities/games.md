## 字段

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
    - 数据类型: `string`
    - 描述: 其他详细信息
    - 约束: JSON 格式
    - 是否必须: 否
    - 示例: `{"key": "value"}`
