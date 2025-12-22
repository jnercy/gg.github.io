# Hexo Admin 使用指南

## 简介
Hexo Admin 是一个强大的网页管理界面，允许你直接在浏览器中编辑和管理 Hexo 博客。

## 快速开始

### 1. 启动 Hexo 服务器
```bash
hexo server
# 或
hexo s
```

### 2. 访问管理界面
打开浏览器，访问：
```
http://localhost:4000/admin
```

### 3. 登录
- **用户名**: `admin`
- **密码**: `admin123`

> ⚠️ **安全提示**: 建议在生产环境中修改默认密码！

## 功能特性

### ✏️ 文章管理
- **创建新文章**: 点击 "New Post" 按钮
- **编辑文章**: 在文章列表中点击文章标题
- **删除文章**: 在编辑页面点击删除按钮
- **草稿管理**: 可以保存为草稿，稍后发布

### 📁 文件管理
- **上传文件**: 支持图片、附件等文件上传
- **文件浏览**: 查看和管理已上传的文件

### 🚀 一键部署
- **快速部署**: 点击 "Deploy" 按钮即可自动执行：
  ```bash
  hexo clean && hexo g && hexo d
  ```

### 📝 Markdown 编辑器
- 实时预览
- 语法高亮
- 支持 Front Matter 编辑

## 修改密码

如果你想修改密码，可以运行以下命令生成新的密码哈希：

```bash
node -e "const bcrypt = require('bcrypt-nodejs'); console.log(bcrypt.hashSync('你的新密码', bcrypt.genSaltSync(10)));"
```

然后将生成的哈希值更新到 `_config.yml` 中的 `admin.password_hash`。

## 配置说明

在 `_config.yml` 中的配置：

```yaml
admin:
  username: admin                    # 登录用户名
  password_hash: $2a$10$...          # 密码哈希（使用 bcrypt）
  secret: jnercy-hexo-admin-secret-key-2024  # 会话密钥
  deployCommand: 'hexo clean && hexo g && hexo d'  # 部署命令
```

## 其他在线编辑方案

### 方案 1: GitHub 在线编辑器
- 直接在 GitHub 仓库中编辑 Markdown 文件
- 提交后需要手动触发部署
- 地址: https://github.com/jnercy/gg.github.io

### 方案 2: StackEdit
- 在线 Markdown 编辑器
- 支持 GitHub 集成
- 地址: https://stackedit.io/

### 方案 3: VS Code Online
- 使用 GitHub Codespaces 或 Gitpod
- 完整的代码编辑体验
- 需要 GitHub 账户

## 注意事项

1. **本地开发**: Hexo Admin 主要用于本地开发环境
2. **安全性**: 不要在生产服务器上暴露 Hexo Admin 端口
3. **备份**: 编辑前建议先备份重要文件
4. **Git 提交**: 编辑后记得提交到 Git 仓库

## 故障排除

### 无法访问 /admin
- 确认 Hexo 服务器正在运行
- 检查端口是否为 4000
- 查看控制台是否有错误信息

### 登录失败
- 检查用户名和密码是否正确
- 确认 `password_hash` 配置正确
- 尝试重新生成密码哈希

### 部署失败
- 检查 Git 配置是否正确
- 确认 SSH 密钥已配置
- 查看部署命令是否正确

## 更多信息

- Hexo Admin GitHub: https://github.com/jaredwray/hexo-admin
- Hexo 官方文档: https://hexo.io/docs/

