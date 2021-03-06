---
id: access_token
title: Access_token API
sidebar_label: Bytom.Access_token.API
---

## create-access-token

创建访问令牌，它为HTTP协议提供基本访问身份验证，返回token包含用户名和密码，它们用冒号分隔。

##### 参数

- `String` - *id*, token ID.

optional:

- `String` - *type*, token类型.

##### 返回

- `String` - *token*, 访问令牌，身份验证用户名和密码（用冒号分隔）.
- `String` - *id*, token ID.
- `String` - *type*, token类型.
- `Object` - *created_at*, token创建时间.

##### 例子
```js
const keyPromise = client.accessTokens.create({
    id:'token1'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
{ id: 'token1',
  token:
   'token1:d15b6975281ba2f9201976b1f7c8f2b3d4c2bf3d9589f14e2c56882d32f5dd83',
  created_at: '2019-04-18T15:39:26.3583019+08:00' }
```

## list-access-tokens

返回所有可用access token的列表。

#### 参数

none

#### 返回

- `Array of Object`, 访问令牌数组.
  - `Object`:
    - `String` - *token*, 访问令牌.
    - `String` - *id*, 令牌id.
    - `String` - *type*, 令牌类型.
    - `Object` - *created_at*, 令牌创建时间.

##### 例子

列出所有可用的access token。
```js
const keyPromise = client.accessTokens.listAll()
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
[
  {
    "token": "token1:1fee70f537128a201338bd5f25a3adbf33dad02eae4f4c9ac43f336a069df8f3",
    "id": "token1",
    "created_at": "2018-03-20T18:56:01.043919771+08:00"
  },
  {
    "token": "alice:78598c6d9fb9e3258d01f78005d4e5725ad0d45e20af90a30b577b407d4a2edd",
    "id": "alice",
    "created_at": "2018-03-20T18:56:01.043919771+08:00"
  }
]
```

## delete-access-token

删除已存在的access token.

#### 参数

`Object`:

- `String` - *id*, 令牌 id.

#### 返回

如果成功删除访问令牌，则为none。

#### 例子

删除access token
```js
const keyPromise = client.accessTokens.delete({
   id:'token1'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
$ node test.js
//response
//none
```


## check-access-token

检查access token有效。

#### 参数

`Object`:

- `String` - *id*, 令牌id.
- `String` - *secret*, secret of token, the second part of the colon division for token.

#### 返回

如果access token被选中有效，则为none。

#### 例子

检查access token是否有效。
```js
const keyPromise = client.accessTokens.check({
     id:'token1',
    secret: '1fee70f537128a201338bd5f25a3adbf33dad02eae4f4c9ac43f336a069df8f3'
})
var sync = keyPromise.then((res) => console.log(res)) 
```
```js
// Result
//none
```