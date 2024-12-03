# Hexo 使用指南

Hexo 是一个快速、简单且功能强大的静态博客框架，适用于生成和部署静态网站。

## 更新博客内容

在更新博客内容时，需要遵循以下步骤：

### 1. 进入 Hexo 项目目录

首先，确保你在 Hexo 项目根目录下：

```bash
cd hexo
```
### 2. 生成静态文件
在进行部署之前，需要使用以下命令生成静态文件：

``` bash
hexo g
```
解释：hexo g 是 hexo generate 的缩写。
该命令会根据 Markdown 文件生成对应的 HTML、CSS 和其他静态资源，并将它们存放在 public/ 目录中。

注意事项：如果出现问题，可以通过以下命令进行调试：
```bash
hexo g --debug
```

### 3. 部署到远程仓库
确保 _config.yml 文件配置正确。
生成静态文件后，需要部署到远程仓库。运行以下命令：

```bash
hexo d
```
解释：hexo d 是 hexo deploy 的缩写。
该命令会将生成的 public/ 文件夹推送到配置文件 _config.yml 中指定的远程仓库。
部署前的检查与配置
#### 1. 安装必要插件
确保已安装 Hexo 的 Git 部署插件：
```bash
npm install hexo-deployer-git --save
```
#### 2. 配置 _config.yml
在 Hexo 项目的 _config.yml 文件中，确保部署部分正确配置：
```bash
deploy:
  type: git
  repo: git@github.com:your-username/your-repo.git
  branch: main
```
type: 必须为 git。
repo: 你的 Git 仓库地址。
branch: 部署的分支，通常为 main 或 gh-pages。

解决常见问题
问题 1: ERROR Deployer not found: git

解决方法：
安装 hexo-deployer-git 插件：
```bash
npm install hexo-deployer-git --save
```
问题 2: 无法连接远程仓库

检查点：确保配置了 SSH 公钥：
```bash
cat ~/.ssh/id_rsa.pub
```
将公钥添加到远程仓库托管平台（如 GitHub）的 SSH 配置中。

测试是否可以正常连接：
``` bash
ssh -T git@github.com
```

## 常用命令总结
|  命令  | 描述  |
|  ----  | ----  |
| hexo clean  | 清理缓存和生成的文件 |
| hexo g  | 生成静态文件 |
| hexo d  | 部署到远程仓库 |
| hexo s  | 本地启动服务器，预览网站 |
| hexo new post "Title"  | 创建新文章 |