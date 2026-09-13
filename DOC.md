# Http API文档

## 登录

### 获取状态

```
GET /api/login/status
```
返回JSON

- `loggedIn`: `boolean` 是否已经登录
- `message`: `string` 信息，无异常时为空字符串
- `loginInProgress`: `boolean` 是否有登录进程

### 开始登录流程

```
POST /api/login/start
```
表单

- `type`: `string` 登录类型，为`"web"`或`"tv"`，不指定则默认为`"web"`

返回JSON

- `ok`: `boolean` 是否正常，若`type`为`"tv"`必定为true
- `type`: `string` 登录类型，为`"web"`或`"tv"`，必定与请求表单中一致
  - 若此项为`"web"`
    - `qrcodeUrl`: `string` 指向登录H5页面的链接，需自行生成二维码
  - 若此项为`"tv"`
    - `qrReady`: `boolean`二维码是否生成完毕，需再次向二维码接口发起请求获取二维码

### 获取二维码图片
