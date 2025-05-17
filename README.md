## 项目简介
<div align="center">
  <img alt="vue3-element-admin" width="80" height="80" src="./src/assets/logo@2x.png">
  <h1>SeerTeach</h1>

  <img src="https://img.shields.io/badge/Vue-3.5.13-brightgreen.svg"/>
  <img src="https://img.shields.io/badge/Vite-6.2.2-green.svg"/>
  <img src="https://img.shields.io/badge/Element Plus-2.9.9-blue.svg"/>
  <img src="https://img.shields.io/badge/license-MIT-green.svg"/>
  <a href="#" target="_blank">
      <img src="https://img.shields.io/badge/Author-SeerTeach-orange.svg"/>
  </a>

</div>

![](https://foruda.gitee.com/images/1708618984641188532/a7cca095_716974.png "rainbow.png")


<div align="center">
  <a target="_blank" href="#">预览后台</a> 
</div>


## 项目简介

[SeerTeach](http://192.168.0.79/Web/weChat.git) 基于 Vue3、Vite、TypeScript 和 Element-Plus 搭建的前端。 


## 项目特色

- **系统功能：** 工作台、设备管理、业务管理，运营管理、系统管理、用户中心
- **权限管理：** 动态路由、按钮权限、角色权限和数据权限等多种权限管理方式。



## 项目截图

🖥️ **工作台**

<img alt="vue3-element-admin" src="./src/assets/example/example1.png">

⚡**用户中心**

<img alt="vue3-element-admin" src="./src/assets/example/example2.png">



## 项目启动


- **环境准备**

| 环境类型       | 名称                     |
|----------------|-----------------------------|
| **开发工具**   | [Visual Studio Code](https://code.visualstudio.com/Download) |
| **运行环境**   | Node 18 + (推荐[22.9.0](https://npmmirror.com/mirrors/node/v22.9.0/))  |
> ⚠️ 注意：Node.js 20.6.0版本存在兼容性问题，请勿使用


- **快速开始**

```bash
# 克隆代码
git clone http://192.168.0.79/Web/weChat.git

# 切换目录
cd weChat

# 安装 pnpm
npm install pnpm -g

# 设置镜像源(可忽略)
pnpm config set registry https://registry.npmmirror.com

# 安装依赖
pnpm install

# 启动运行
pnpm run dev
```


## 项目部署

执行 `pnpm run build` 命令后，项目将被打包并生成 `dist` 目录。接下来，将 `dist` 目录下的文件上传到服务器 `/usr/share/nginx/html` 目录下，并配置 Nginx 进行反向代理。

```bash
pnpm run build
```

以下是 Nginx 的配置示例：

```nginx
server {
    listen      80;
    server_name localhost;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    # 反向代理配置
    location /prod-api/ {
        # 请将 api.youlai.tech 替换为您的后端 API 地址，并注意保留后面的斜杠 /
        proxy_pass http://api.youlai.tech/;
    }
}
```

更多详细信息，请参考这篇文章：[Nginx 安装和配置](https://blog.csdn.net/u013737132/article/details/145667694)。

## 本地Mock

项目同时支持在线和本地 Mock 接口，默认使用线上接口，如需替换为 Mock 接口，修改文件 `.env.development` 的 `VITE_MOCK_DEV_SERVER` 为  `true` **即可**。