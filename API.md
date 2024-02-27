API接口仅提供https版本，请求体统一使用JSON格式

非最终版，可能在请求头添加鉴权、时间戳等信息，

修改请求方法，增加可选参数，增加新的API，

对已有的API进行改动（尽量避免）等

用户 users：

POST /api/v1/users 注册用户

DETELE /api/v1/users/{user-id} 永久注销用户

PUT /api/v1/users/login 登录用户

DELETE /api/v1/users/{user-id}/logout 登出用户

GET /api/v1/users?[page={page}]&[page-size={page-size}]&[sort=user-id|asc]&[keyword=…]

查询用户表，需要额外鉴权，keyword用于user-name模糊匹配，[]表示可选项，sort默认asc，如果有时间则可能还会添加对行/列的过滤功能

GET /api/v1/users/{user-id} 查询用户信息，包括user-id、user-name、is-admin等

PUT /api/v1/users/{user-id} 修改用户信息

PUT /api/v1/users/{user-id}/change-password 修改密码

游戏 games：

GET /api/v1/games?[page={page}]&[page-size={page-size}]&[sort=user-id|asc]&[keyword=…]

查询游戏列表

GET /api/v1/games/{game-id} 查询游戏信息

GET /api/v1/games/{game-id}/rankings 查询游戏排行榜

GET /api/v1/games/{game-id}/…    // TODO 查询其他信息

POST /api/v1/games 新增游戏（可能硬编码）（可能需上传文件）（需鉴权）

DELETE /api/v1/games/{game-id} 删除游戏（可能硬编码）（需鉴权）

游戏若做成单机，则只需添加静态资源，若需要联机，则需要创建独立的后端进行处理，可将后端打包为Docker镜像

PUT /api/v1/games/{game-id} 修改游戏信息（需鉴权）

POST /api/v1/games-onshelves 上架游戏（将启动Docker容器）（需鉴权）

DELETE /api/v1/games-onshelves/{game-id} 下架游戏（需鉴权）

房间 rooms：

GET /api/v1/rooms?game={game-id}&[page={page}]&[page-size={page-size}]&[sort=user-id|asc]&[keyword=…]  查询房间列表

// TODO 查询房间列表时，关联的游戏id应为必填项还是可选项？

GET /api/v1/rooms/{room-id} 查询房间信息，无需游戏id

POST /api/v1/rooms?game={game-id} 创建房间

PUT /api/v1/rooms/{room-id} 修改房间信息（仅房主？）

DELETE /api/v1/rooms/{room-id} 删除房间（仅房主）

PUT /api/v1/rooms/{room-id}/join 加入房间

PUT /api/v1/rooms/{room-id}/leave 离开房间