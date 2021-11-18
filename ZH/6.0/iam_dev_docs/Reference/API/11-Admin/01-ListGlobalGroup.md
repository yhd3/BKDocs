# 超级管理类 API
### 查询用户组列表
-------

#### URL

> GET /api/c/compapi/v2/iam/admin/groups/
> `特别说明:该 API 为ESB API` [ESB API 说明](../01-Overview/01-BackendAPIvsESBAPI.md)


#### Parameters

* 通用参数

| 字段 |  类型 |是否必须  | 描述  |
|--------|--------|--------|--------|
|bk_app_code|string|是|应用 ID|
|bk_app_secret|string|是|安全密钥(应用 TOKEN)，可以通过 蓝鲸智云开发者中心 -> 点击应用 ID -> 基本信息 获取|
|bk_token|string|否|当前用户登录态，bk_token 与 bk_username 必须一个有效，bk_token 可以通过 Cookie 获取|
|bk_username|string|否|当前用户用户名，仅仅在 ESB 里配置免登录态验证白名单中的应用，才可以用此字段指定当前用户|

* 接口参数

| 字段 |  类型 |是否必须  | 位置 |描述  |
|--------|--------|--------|--------|--------|
| limit |  int  | 是   | query |分页查询参数之一，limit 表示查询数量，`最大值为100` |
| offset  | int | 是 | query | 分页查询参数之一，offset 表示从第几个开始查询，offset 从 0 开始计算 |
| id | int | 否 | query | 过滤的用户组 ID | 
| name | string | 否 | query | 用于搜索的用户组名称 |
| description | string | 否 | query | 用于搜索的用户组描述 |
| grade_manager_id | int | 否 | query | 用于过滤某个分级管理员下用户组 |


#### Request
```plain
Get /api/c/compapi/v2/iam/admin/groups/?offset=0&limit=10
```

#### Response

| 字段      | 类型      | 描述      |
|-----------|-----------|-----------|
| count   |  int     |  总数量 |
| results   |  array[object]   |  分页查询到结果 |

results
| 字段      | 类型      | 描述      |
|-----------|-----------|-----------|
| id   | int     | 用户组 ID |
| name | string | 用户组名称 |
| description | string | 用户组描述 |


> Status: 200 OK

```json
{
 ​"code": 0,
 ​"message": "ok",
 ​"data": {
   ​"count": 3,
   ​"results": [
     ​{
       ​"id": 1,
       ​"name": "test1",
       ​"description": "test1"
     ​},
     ​{
       ​"id": 2,
       ​"name": "test2",
       ​"description": "test2"
     ​},
     ​{
       ​"id": 2,
       ​"name": "test2",
       ​"description": "test"
     ​},
   ​]
 ​}
}
```