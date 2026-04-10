# Todo

## 网站部署全流程（GitHub + Cloudflare Pages）

### 第 0 步：先确认本地项目没问题
本地预览统一使用：

```bash
cd "/home/yukikaze/Documents/workspace/homepage"
python3 -m http.server 8000
```

浏览器打开：

```text
http://127.0.0.1:8000/
```

先确认这些都正确：
- 标题、名字、footer 已经是你想要的内容
- 图片正常显示
- GitHub / Mail / 卡片链接正常
- 页面布局在电脑端和手机端都没有明显问题

---

### 第 1 步：准备 GitHub 仓库
进入真实工作目录：

```bash
cd "/home/yukikaze/Documents/workspace/homepage"
git status
```

如果你还没有自己的 GitHub 仓库：
1. 打开 GitHub
2. 新建一个仓库，例如：
   - `homepage`
   - `yukikaze-homepage`

如果当前远程仓库不是你的，绑定成你自己的仓库：

```bash
git remote remove origin
git remote add origin https://github.com/Yukikaze2233/homepage.git
```

检查远程仓库：

```bash
git remote -v
```

---

### 第 2 步：把当前网站代码推到 GitHub
```bash
cd "/home/yukikaze/Documents/workspace/homepage"
git add .
git commit -m "feat: personalize homepage"
git push -u origin main
```

如果提示当前分支不是 `main`，先确认当前分支名：

```bash
git branch
```

如果需要推送当前分支，也可以用：

```bash
git push -u origin HEAD
```

---

### 第 3 步：注册并登录 Cloudflare
打开：

```text
https://dash.cloudflare.com/
```

如果没有账号就先注册，有账号就直接登录。

---

### 第 4 步：在 Cloudflare Pages 创建项目
1. 进入 **Workers & Pages**
2. 点击 **Create application**
3. 选择 **Pages**
4. 选择 **Connect to Git**
5. 授权 Cloudflare 访问你的 GitHub
6. 选择仓库：`Yukikaze2233/homepage`

---

### 第 5 步：填写构建配置
因为这个项目是纯静态站，所以配置非常简单：

- **Framework preset**: `None`
- **Build command**: 留空
- **Build output directory**: `/`
- **Root directory**: 留空

然后点击部署。

---

### 第 6 步：第一次上线后验证 Pages 临时域名
部署成功后，Cloudflare Pages 会生成一个临时域名，例如：

```text
xxxxx.pages.dev
```

打开这个地址，检查：
- 页面能打开
- 名字、标题、footer 正确
- 所有图片都能加载
- GitHub / Mail / 项目卡片跳转正常
- 手机端显示没有明显错位

如果这里显示正常，说明网站已经可以公开访问。

---

### 第 7 步：购买域名（如果你还没有）
可以在这些平台购买：
- 阿里云万网
- 腾讯云 DNSPod
- Cloudflare Registrar
- Namecheap

建议后缀：
- `.com`
- `.net`
- `.dev`
- `.me`

---

### 第 8 步：把域名接入 Cloudflare
如果你的域名还不在 Cloudflare：
1. 在 Cloudflare 添加你的域名
2. 按提示把域名的 Nameserver 改到 Cloudflare
3. 等 DNS 生效

如果域名已经在 Cloudflare，就直接下一步。

---

### 第 9 步：给 Pages 绑定自定义域名
在 Cloudflare Pages 项目中：
1. 进入项目详情页
2. 找到 **Custom domains**
3. 点击 **Set up a custom domain**
4. 输入你的域名，例如：
   - `yukikaze.net`
   - `www.yukikaze.net`

Cloudflare 一般会自动处理需要的 DNS 记录。

---

### 第 10 步：验证自定义域名和 HTTPS
等待解析完成后，检查：

- `https://yourdomain.com` 是否能打开
- `https://www.yourdomain.com` 是否能打开（如果你绑定了）
- HTTPS 证书是否正常
- 页面资源是否完整加载

---

### 第 11 步：以后怎么更新网站
以后每次改网站，只需要：

```bash
cd "/home/yukikaze/Documents/workspace/homepage"
git add .
git commit -m "feat: update homepage"
git push
```

推送后：
- GitHub 更新代码
- Cloudflare Pages 自动重新部署
- 几分钟后线上网站自动更新

---

### 第 12 步：每次更新后的检查清单
每次上线后建议检查：
- 标题和名字是否正确
- 图片是否正常
- GitHub / Mail / 项目卡片链接是否可用
- 手机端是否错位
- 浏览器控制台是否有明显报错

---

## 如果后续改动很多，推荐工作流
1. 本地修改 `homepage`
2. 用 `python3 -m http.server 8000` 本地验证
3. 满意后 `git commit` + `git push`
4. 等 Cloudflare Pages 自动部署
5. 用正式域名复查

---

## plan.md 精简大纲

### 目标
- 基于原模板搭建自己的主页，并持续维护上线

### 阶段
1. 工作目录统一
   - 只在 `homepage` 修改
   - 用本地 HTTP 预览

2. 品牌替换
   - 标题
   - 名字
   - footer
   - GitHub / Mail

3. 内容替换
   - 介绍文案
   - 左侧信息
   - 时间线
   - 项目卡片

4. 资源替换
   - 头像
   - 背景
   - 卡片图片
   - 其他素材

5. 上线部署
   - GitHub
   - Cloudflare Pages
   - 自定义域名

### 当前下一步
- 完善剩余卡片和链接
- 清理原模板残留内容
- 接入 GitHub + Cloudflare Pages

---

## code.md 精简步骤

1. 分析模板结构
   - 确认是静态 HTML/CSS/JS 项目

2. 确认实际工作目录
   - 真实预览目录是 `homepage`
   - `homepage --1` 不再作为修改目标

3. 完成基础品牌替换
   - 标题改为 `Yukikaze`
   - 中间名字改为 `Yukikaze`
   - footer 改为 `Yukikaze © 2026 |`

4. 完成左侧信息精简
   - `China-Nanjin`
   - 删除 `Sias`
   - 删除标签框
   - 时间线仅保留一条

5. 完成首页介绍替换
   - 改为算法工程 / 机器人 / 视觉方向介绍

6. 完成卡片初步替换
   - 博客
   - Team
   - `妙妙小站点`
   - `sakuracat`
   - `DokiDokiWeb`

7. 记录本地预览经验
   - 不再用 `file://`
   - 统一用 `python3 -m http.server 8000`

8. 下一步
   - 接入 GitHub
   - 配置 Cloudflare Pages
   - 绑定域名
