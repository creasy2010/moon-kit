# moon-kit

### Vue/js 版本调用

这是一个前后端 API 接口调用工具，通过此工具可以根据 swagger-json 直接生成接口的调用方法（暴露统一入口，以 controller 区分文件）
生成的结果

1. 具备完善的 TS 参数类型定义，（基于后端 JAVA 注解）
2. 前端调用接口，不区分接口涉及到的 请求方法（ method ）、入参的形式（ query？、param？、body？、path？ ）

#### 调用方式

```js
// 引入API对象
import api from "@/api";

/**
 * 调用接口
 */
const res = await api.guideController.getGuide({ guideCode: id });
```

#### 生成接口

使用 cli 脚本生成对应的接口，
生成接口的命令

```bash
npm run api
```

配置文件：moon-config.js

```js
module.exports = {
  type: "h5-redux",
  api: {
    // 支持多个swagger-api-docs地址
    swaggerUrls: [
      "http://47.116.5.18:9001/user/v2/api-docs",
      "http://47.116.5.18:9001/customer/v2/api-docs",
    ],
    plugins: [],
    dir: "./src/api-ts",
    mock: {
      ignoreApi: [],
    },
    exclude: [],
    //  每次只会生成 include 数组包括的 controller,可以包含多个，如果不填则会全部重新生成！！！
    include: ["GuideController"],
  },
};
```
