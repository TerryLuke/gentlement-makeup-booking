# GitHub Pages 部署说明

本项目已配置自动部署到 GitHub Pages，可以通过以下步骤启用和访问。

## 🚀 自动部署配置

### GitHub Actions 工作流
- **文件位置**: `.github/workflows/deploy.yml`
- **触发条件**: 
  - 推送到 `main` 分支时自动触发
  - 支持手动触发部署
- **部署内容**: 将 `prototype-v2/` 目录下的文件部署到根目录

### 部署流程
1. **构建阶段**:
   - 检出代码
   - 将 `prototype-v2/` 目录下的文件复制到根目录
   - 创建项目导航页面 (`nav.html`)
   - 上传构建产物

2. **部署阶段**:
   - 部署到 GitHub Pages
   - 生成访问链接

## 📋 启用步骤

### 1. 启用 GitHub Pages

**重要**: 必须先手动启用GitHub Pages才能使用自动部署！

详细步骤：
1. **进入仓库设置**
   - 访问: `https://github.com/TerryLuke/gentlement-makeup-booking`
   - 点击 **Settings** 标签页（在仓库顶部导航栏）

2. **找到Pages设置**
   - 在左侧菜单中向下滚动找到 **Pages** 选项
   - 点击进入Pages配置页面

3. **配置部署源**
   - 在 **Source** 下拉菜单中选择 **GitHub Actions**
   - 不要选择 "Deploy from a branch"
   - 确保选择了 "GitHub Actions" 选项

4. **保存配置**
   - 点击 **Save** 按钮
   - 页面会显示站点将发布到的URL

5. **确认设置**
   - 设置成功后会看到绿色提示
   - 显示类似: "Your site is ready to be published at https://terryluke.github.io/gentlement-makeup-booking/"

### 2. 部署触发
- **自动部署**: 每次推送到 `main` 分支时自动触发
- **手动部署**: 
  1. 进入 **Actions** 标签页
  2. 选择 **Deploy to GitHub Pages** 工作流
  3. 点击 **Run workflow** 按钮

### 3. 访问站点
部署完成后，可以通过以下链接访问：
- **主站点**: `https://{username}.github.io/{repository-name}/`
- **项目导航**: `https://{username}.github.io/{repository-name}/nav.html`

## 🎯 页面结构

部署后的站点包含以下页面：

### 主要页面
- **index.html**: 用户端小程序原型
- **artist-app.html**: 美甲师工作台原型  
- **admin-dashboard.html**: 管理后台原型
- **nav.html**: 项目导航页面（自动生成）

### 访问路径
```
https://{username}.github.io/{repository-name}/
├── index.html              # 主页 - 用户端
├── nav.html                # 导航页面
├── artist-app.html         # 美甲师端
├── admin-dashboard.html    # 管理后台
└── README.md              # 项目说明
```

## 🔧 自定义配置

### 修改部署源
如果需要从其他目录部署，可以修改 `.github/workflows/deploy.yml` 文件中的复制命令：

```yaml
- name: Copy prototype files to root
  run: |
    # 修改这里的源目录
    cp -r prototype-v2/* .
```

### 添加自定义域名
1. 在仓库根目录创建 `CNAME` 文件
2. 在文件中写入自定义域名
3. 在域名提供商处配置 DNS 记录

### 环境变量
工作流中可以使用以下环境变量：
- `GITHUB_TOKEN`: 自动提供的访问令牌
- `GITHUB_REPOSITORY`: 仓库名称
- `GITHUB_SHA`: 提交的 SHA 值

## 📊 监控部署

### 查看部署状态
1. 进入 **Actions** 标签页
2. 查看最新的工作流运行状态
3. 点击具体的运行记录查看详细日志

### 部署失败排查
常见问题及解决方案：

1. **权限问题**:
   - 确保在仓库设置中启用了 Actions 权限
   - 检查 Pages 权限设置

2. **文件路径问题**:
   - 确认 `prototype-v2/` 目录存在
   - 检查 `index.html` 文件是否存在

3. **构建失败**:
   - 查看 Actions 日志中的错误信息
   - 检查文件编码和格式是否正确

## 🎉 访问示例

假设仓库信息如下：
- 用户名: `nicemakeuper`
- 仓库名: `gentlement-makeup-booking`

部署后的访问链接：
- 主站点: `https://nicemakeuper.github.io/gentlement-makeup-booking/`
- 导航页: `https://nicemakeuper.github.io/gentlement-makeup-booking/nav.html`
- 用户端: `https://nicemakeuper.github.io/gentlement-makeup-booking/index.html`
- 美甲师端: `https://nicemakeuper.github.io/gentlement-makeup-booking/artist-app.html`
- 管理后台: `https://nicemakeuper.github.io/gentlement-makeup-booking/admin-dashboard.html`

---

*部署完成后，每次推送到 main 分支都会自动更新站点内容。*
