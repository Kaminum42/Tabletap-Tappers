# 查询用户

## 说明

查询用户

## 要求

登录认证: 可选

身份 / 权限: 可选

非本人或管理员只可查看公开信息

## 请求方法

`GET`

## 路径

`/api/v1/users/{user_id}`

- `user_id`
    - 数据类型: `number`
    - 描述: 用户ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `10000`


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
GET /api/v1/users/{user_id} HTTP/1.1
...
```

## 响应头

### 响应状态码

- `200`: 查找成功

- `400`: 请求格式不正确

- `404`: 找不到该用户

- `429`: 请求过于频繁

- `500`: 服务器内部错误

### 字段说明

无

## 响应体

响应体类型: `application/json`

### 字段说明

- `user_id`
    - 数据类型: `number`
    - 描述: 用户 ID
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `10000`
 
- `username`
    - 数据类型: `string`
    - 描述: 用户名, 唯一且不可更改
    - 约束: 长度 4-32 , 允许字符为大小写英文, 数字, 下划线 `_` 和连字符 `-`
    - 是否必须: 是
    - 示例: `zhangsan`

- `permission_level`
    - 数据类型: `number`
    - 描述: 权限等级, 0 ~ 99 system, 100 ~ 199 admin, 200 ~ 299 server, 300 ~ 399 user, 400 ~ 499 guest, 其余保留
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 是
    - 示例: `0`

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

- `create_time`
    - 数据类型: `number`
    - 描述: 用户创建时间, `profile_visibility` 为 `false` 时不可见
    - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
    - 是否必须: 否
    - 示例: `1704038400000`

- `update_time`
    - 数据类型: `number`
    - 描述: 用户档案更新时间, `profile_visibility` 为 `false` 时不可见
    - 约束: 时间戳(ms), 整数, 0 ~ 2^64-1
    - 是否必须: 否
    - 示例: `1704038400000`

- `experience`
    - 数据类型: `number`
    - 描述: 经验值, `profile_visibility` 为 `false` 时不可见
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 否
    - 示例: `100`

- `level`
    - 数据类型: `number`, `profile_visibility` 为 `false` 时不可见
    - 描述: 等级, 与经验值换算关系为 `y = 0.2xlnx + 10`
    - 约束: 整数, 0 ~ 2^32-1
    - 是否必须: 否
    - 示例: `10`

- `icon_url`
    - 数据类型: `string`
    - 描述: 头像文件的地址, `profile_visibility` 为 `false` 时不可见
    - 约束: 合法的 URL
    - 是否必须: 否
    - 示例: `100`

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
    - 描述: 用户档案可见性, `true` 为公开, `false` 为不公开
    - 约束: `true` 或者 `false`
    - 是否必须: 是
    - 示例: `true`

- `details`
    - 数据类型: `Object`
    - 描述: 其他详细信息, `profile_visibility` 为 `false` 时不可见
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
    "body": {
        "user_id": 1,
        "username": "zhangsan",
        "permission_level": 400,
        "nickname": "张三",
        "email": "123456@qq.com",
        "create_time": 1704038400000,
        "update_time": 1704038400000,
        "experience": 100,
        "level": 10,
        "icon_url": "...",
        "gender": "男",
        "birthday": 1704038400000,
        "phone": "13912345678",
        "address": "上海市浦东新区",
        "profile_visibility": true,
        "details": {
            "key": "value"
        }
    }
}
```