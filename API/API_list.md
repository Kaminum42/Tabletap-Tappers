API接口仅提供https版本，请求体统一使用JSON格式

非最终版，可能在请求头添加鉴权、时间戳等信息，

修改请求方法，增加可选参数，增加新的API，

对已有的API进行改动（尽量避免）等

## 用户 (users)

| 方法 | 路径 | 说明 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| POST | /api/v1/users | 注册用户 | √ |
| DELETE | /api/v1/users/{user_id} | 永久注销用户 | √ |
| POST | /api/v1/users/get_user_id | 根据用户名 / 邮箱获取ID | √ |
| GET | /api/v1/users/{user_id}/password_salt | 获取传输密码用的盐 | √ |
| POST | /api/v1/users/login | 登录用户 | √ |
| POST | /api/v1/users/{user_id}/logout | 登出用户 | √ |
| GET | /api/v1/users?[page={page}]&[page_size={page_size}]&[sort=user_id\|asc]&[keyword=…] | 查询用户表，需要额外鉴权，keyword用于username模糊匹配，[]表示可选项，sort默认asc，如果有时间则可能还会添加对行/列的过滤功能 | √ |
| GET | /api/v1/users/{user_id} | 查询用户信息，包括user-id、user-name、is-admin等 | √ |
| PUT | /api/v1/users/{user_id} | 修改用户信息 | √ |
| POST | /api/v1/users/{user_id}/change_password | 修改密码 | √ |
| POST | /api/v1/users/{user_id}/verify_email | 验证邮箱 | × |
| POST | /api/v1/users/{user_id}/retrive_password | 找回密码 | × |
| POST | /api/v1/users/{user_id}/upload_icon | 上传头像 | × |
| GET | /api/v1/users/current | 获取当前用户信息 | × |
| POST | /api/v1/users/current/ping | 登录测试 | × |

## 游戏 (games)

游戏若做成单机，则只需添加静态资源，若需要联机，则需要创建独立的后端进行处理，可将后端打包为Docker镜像

| 方法 | 路径 | 说明 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| GET | /api/v1/games?[page={page}]&[page_size={page_size}]&[sort=game_id\|asc]&[keyword=…] | 查询游戏列表 | √ |
| GET | /api/v1/games/{game_id} | 查询游戏信息 | √ |
| POST | /api/v1/game/{game_id}/upload_icon | 上传游戏图标（需鉴权） | × |
| POST | /api/v1/game/{game_id}/upload_cover | 上传游戏封面（需鉴权） | × |
| PUT | /api/v1/games/{game_id} | 修改游戏信息（需鉴权） | √ |
| POST | /api/v1/games/{game_id}/open | 上架游戏（将启动Docker容器）（需鉴权） | √ |
| DELETE | /api/v1/games/{game_id}/close | 下架游戏（需鉴权） | √ |

## 对局 (rounds)
| 方法 | 路径 | 描述 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| GET | /api/v1/rounds?[game={game_id}]&[user={user_id}]&[page={page}]&[page_size={page_size}]&[sort=create_time\|desc] | 查询对局列表 | √ |
| GET | /api/v1/rounds/{round_id} | 查询对局信息（仅参与者?） | √ |
| POST | /api/v1/rounds | 创建对局记录 | √ |
| DELETE | /api/v1/rounds/{round_id} | 删除对局记录（允许吗?） | √ |

## 排行榜 (rankings)
| 方法 | 路径 | 描述 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| GET | /api/v1/rankings?[game={game_id}]&[user={user_id}]&[page={page}]&[page_size={page_size}]&[sort=total_score\|desc,update_time\|desc] | 查询排行榜 | √ |

## 公告 (announcements)
| 方法 | 路径 | 描述 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| GET | /api/v1/announcements?[page={page}]&[page_size={page_size}]&[sort=update_time\|desc]&[keyword=…] | 查询公告列表 | √ |
| GET | /api/v1/announcements/{announcement_id} | 查询公告信息 | √ |
| POST | /api/v1/announcements | 发布公告 | √ |
| PUT | /api/v1/announcements/{announcement_id} | 修改公告 | √ |
| DELETE | /api/v1/announcements/{announcement_id} | 删除公告 | √ |

## 评论 (comments)
| 方法 | 路径 | 描述 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| GET | /api/v1/comments?game={game_id}&[page={page}]&[page_size={page_size}]&[sort=create_time\|desc] | 查询评论列表 | √ |
| GET | /api/v1/comments/{comment_id} | 查询评论信息 | √ |
| POST | /api/v1/comments | 发布评论 | √ |
| DELETE | /api/v1/comments/{comment_id} | 删除评论 | √ |

## 私信 (messages)
| 方法 | 路径 | 描述 | 是否有文档 |
| ---- | ---- | ---- | ---- |
| GET | /api/v1/messages?[from_user={user_id}]&[to_user={user_id}]&[page={page}]&[page_size={page_size}]&[sort=send_time\|desc] | 查询私信列表 | √ |
| GET | /api/v1/messages/{message_id} | 查询私信信息 | √ |
| POST | /api/v1/messages | 发送私信 | √ |
| DELETE | /api/v1/messages/{message_id} | 删除私信 | √ |
| GET | /api/v1/messages/contacts?user={user_id} | 查询私信联系人列表 | × |