# 子频道权限对象(ChannelPermissions)

### ChannelPermissions

| 字段名      | 类型   | 描述                                                        |
| ----------- | ------ | ----------------------------------------------------------- |
| channel_id  | string | 子频道 ID                                                   |
| user_id     | string | 用户 ID                                                     |
| permissions | string | 用户拥有的子频道权限，具体值参考[permissions](#permissions) |

### Permissions

权限是 QQ 频道管理频道成员的一种方式，管理员可以对不同的人、不同的子频道设置特定的权限。用户的权限包括**个人权限**和**身份组权限**两部分，最终生效是取两种权限的并集。

权限使用位图表示，传递时序列化为十进制数值字符串。如权限值为`0x6FFF`，会被序列化为十进制`"28671"`。

| 权限         | 值                    | 描述                                                 |
| ------------ | --------------------- | ---------------------------------------------------- |
| 可查看子频道 | 0x0000000001 (1 << 0) | 目前仅支持`指定成员`可见类型，不支持`身份组`可见类型 |
| 可管理子频道 | 0x0000000002 (1 << 1) | 创建者、管理员、子频道管理员都具有此权限             |

##### 参数参考

| 字段名 | 类型   | 描述                               |
| ------ | ------ | ---------------------------------- |
| add    | string | 字符串形式的位图表示赋予用户的权限 |
| remove | string | 字符串形式的位图表示删除用户的权限 |
