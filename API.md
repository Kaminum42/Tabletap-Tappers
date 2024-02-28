API接口仅提供https版本，请求体统一使用JSON格式

非最终版，可能在请求头添加鉴权、时间戳等信息，

修改请求方法，增加可选参数，增加新的API，

对已有的API进行改动（尽量避免）等

## 用户 (users)

| 方法 | 路径 | 说明 |
| ---- | ---- | ---- |
| POST | /api/v1/users | 注册用户 |
| DELETE | /api/v1/users/{user-id} | 永久注销用户 |
| PUT | /api/v1/users/login | 登录用户 |
| DELETE | /api/v1/users/{user-id}/logout | 登出用户 |
| GET | /api/v1/users?[page={page}]&[page-size={page-size}]&[sort=user-id\|asc]&[keyword=…] | 查询用户表，支持分页、排序、关键字模糊匹配 |
| GET | /api/v1/users/{user-id} | 查询用户信息，包括user-id、user-name、is-admin等 |
| PUT | /api/v1/users/{user-id} | 修改用户信息 |
| PUT | /api/v1/users/{user-id}/change-password | 修改密码 |


## 游戏 (games)

| 方法 | 路径 | 说明 |
| ---- | ---- | ---- |
| GET | /api/v1/games?[page={page}]&[page-size={page-size}]&[sort=user-id\|asc]&[keyword=…] | 查询游戏列表 |
| GET | /api/v1/games/{game-id} | 查询游戏信息 |
| GET | /api/v1/games/{game-id}/rankings | 查询游戏排行榜 |
| GET | /api/v1/games/{game-id}/… | TODO: 查询其他信息 |
| POST | /api/v1/games | 新增游戏（可能需上传文件，需鉴权） |
| DELETE | /api/v1/games/{game-id} | 删除游戏（需鉴权） |
| PUT | /api/v1/games/{game-id} | 修改游戏信息（需鉴权） |
| POST | /api/v1/games-onshelves | 上架游戏（需鉴权） |
| DELETE | /api/v1/games-onshelves/{game-id} | 下架游戏（需鉴权） |

## 房间 (rooms)
| 方法 | 路径 | 描述 |
| ---- | ---- | ---- |
| GET | /api/v1/rooms?game={game-id}&[page={page}]&[page-size={page-size}]&[sort=user-id\|asc]&[keyword=…] | 查询房间列表 |
| GET | /api/v1/rooms/{room-id} | 查询房间信息 |
| POST | /api/v1/rooms?game={game-id} | 创建房间 |
| PUT | /api/v1/rooms/{room-id} | 修改房间信息（仅房主） |
| DELETE | /api/v1/rooms/{room-id} | 删除房间（仅房主） |
| PUT | /api/v1/rooms/{room-id}/join | 加入房间 |
| PUT | /api/v1/rooms/{room-id}/leave | 离开房间 |
