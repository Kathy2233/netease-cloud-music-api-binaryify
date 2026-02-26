# 网易云音乐 API

网易云音乐 Node.js API service

## 灵感来自

[disoul/electron-cloud-music](https://github.com/disoul/electron-cloud-music)

[darknessomi/musicbox](https://github.com/darknessomi/musicbox)

[sqaiyan/netmusic-node](https://github.com/sqaiyan/netmusic-node)

[greats3an/pyncm](https://github.com/greats3an/pyncm)


## 环境要求

需要 NodeJS 14+ 环境

## 安装

```shell
$ git clone https://github.com/Kathy2233/netease-cloud-music-api-binaryify.git
# cd 进入克隆的文件夹
$ npm install
```

## 运行

```shell
$ node app.js
```

服务器启动默认端口为 3000,若不想使用 3000 端口,可使用以下命令: Mac/Linux

```shell
$ PORT=4000 node app.js
```

windows 下使用 git-bash 或者 cmder 等终端执行以下命令:

```shell
$ set PORT=4000 && node app.js
```

## 演示
```shell
ubuntu@Laptopcl:~/neteasemmusicapi/NeteaseCloudMusicApi$ nvm -v
0.40.3
ubuntu@Laptopcl:~/neteasemmusicapi/NeteaseCloudMusicApi$ node -v
v14.21.3
ubuntu@Laptopcl:~/neteasemmusicapi/NeteaseCloudMusicApi$ npm -v
6.14.18
ubuntu@Laptopcl:~/neteasemmusicapi/NeteaseCloudMusicApi$ npm install
npm WARN read-shrinkwrap This version of npm is compatible with lockfileVersion@1, but package-lock.json was generated for lockfileVersion@2. I'll try to do my best with it!

> core-js@2.6.12 postinstall /home/ubuntu/neteasemmusicapi/NeteaseCloudMusicApi/node_modules/core-js
> node -e "try{require('./postinstall')}catch(e){}"

Thank you for using core-js ( https://github.com/zloirock/core-js ) for polyfilling JavaScript standard library!

The project needs your help! Please consider supporting of core-js on Open Collective or Patreon:
> https://opencollective.com/core-js
> https://www.patreon.com/zloirock

Also, the author of core-js ( https://github.com/zloirock ) is looking for a good job -)


> NeteaseCloudMusicApi@4.25.0 prepare /home/ubuntu/neteasemmusicapi/NeteaseCloudMusicApi
> husky install

husky - Git hooks installed
npm WARN NeteaseCloudMusicApi@4.25.0 No repository field.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.3.3 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.3.3: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 22 packages from 130 contributors and audited 564 packages in 3.355s

111 packages are looking for funding
  run `npm fund` for details

found 63 vulnerabilities (19 low, 16 moderate, 26 high, 2 critical)
  run `npm audit fix` to fix them, or `npm audit` for details
ubuntu@Laptopcl:~/neteasemmusicapi/NeteaseCloudMusicApi$ node app
最新版本: 4.29.0, 当前版本: 4.25.0, 请及时更新
server running @ http://localhost:3000

```

## Vercel 部署

v4.0.8 加入了 Vercel 配置文件,可以直接在 Vercel 下部署了,不需要自己的服务器

### 操作方法

1. fork 此项目
2. 在 Vercel 官网点击 `New Project`
3. 点击 `Import Git Repository` 并选择你 fork 的此项目并点击`import`
4. 点击 `PERSONAL ACCOUNT` 的 `select`
5. 直接点`Continue`
6. `PROJECT NAME`自己填,`FRAMEWORK PRESET` 选 `Other` 然后直接点 `Deploy` 接着等部署完成即可  

## 腾讯云 serverless 部署
因 `Vercel` 在国内访问太慢,在此提供腾讯云 serverless 部署方法(注意:腾讯云 serverless 并不是免费的,前三个月有免费额度,之后收费)
### 操作方法
1. fork 此项目
2. 在腾讯云serverless应用管理页面( https://console.cloud.tencent.com/sls ),点击`新建应用`
3. 顶部`创建方式`选择 `Web 应用`
4. 选择 `Express框架`,点击底部`下一步按钮`
5. 输入`应用名`,上传方式选择`代码仓库`,进行GitHub授权(如已授权可跳过这一步),代码仓库选择刚刚fork的项目
6. 启动文件填入:
```
#!/bin/bash
export PORT=9000
/var/lang/node16/bin/node app.js
``` 
7. 点击`完成`,等待部署完成,点击`资源列表`的 `API网关` 里的 `URL`,正常情况会打开文档地址,点击文档`例子`可查看接口调用效果

## 可以在Node.js调用

v3.31.0后支持Node.js调用,导入的方法为`module`内的文件名,返回内容包含`status`和`body`,`status`为状态码,`body`为请求返回内容,参考`module_example` 文件夹下的 `test.js`

```js
const { login_cellphone, user_cloud } = require('NeteaseCloudMusicApi')
async function main() {
  try {
    const result = await login_cellphone({
      phone: '手机号',
      password: '密码'
    })
    console.log(result)
    const result2 = await user_cloud({
      cookie: result.body.cookie // 凭证
    })
    console.log(result2.body)
      
  } catch (error) {
    console.log(error)
  }
}
main()
```

## 支持 TypeScript

```ts
// test.ts
import { banner } from 'NeteaseCloudMusicApi'
banner({ type:0 }).then(res=>{
  console.log(res)
})
```


## 使用文档

部署后访问API的IP:PORT即可看到。

## 功能特性

见使用文档。

## License

The MIT License (MIT)
