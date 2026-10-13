# 小艺 · 自我介绍页

二次元风格的**单页个人网站**，背景使用插画，全站使用自定义中文字体「字魂流氓兔体」。

## 🌸 在线访问

**<https://mcharaorz.github.io/YXB-intro/>**

仓库地址：<https://github.com/MCharaorz/YXB-intro>

## 文件结构

```
index.html                 单页网站（HTML / CSS / JS 全部内联，零依赖）
assets/bg.png              背景插画
assets/fonts/liulangtu.ttf 自定义字体：字魂流氓兔体
README.md                  本说明
upload.mjs                 上传/更新脚本（走 GitHub API，不需要 git）
deploy-github.mjs          首次建仓库用的脚本
```

## 本地查看

直接双击 `index.html` 用浏览器打开即可，**不需要任何服务器或构建步骤**。

## 怎么更新线上内容

改完 `index.html` 后，在项目目录运行：

```powershell
$env:GH_TOKEN = "你的token"; $env:GH_OWNER = "MChara520"; $env:GH_REPO = "YXB-intro"
& "C:\Users\MChara\.dsh\dsh-runtimes\dsh-primary-runtime\dependencies\node\bin\node.exe" upload.mjs
```

脚本会先自检写权限，再逐个上传变更的文件。GitHub Pages 会在 1~2 分钟内自动重新构建。

> token 需要 `Contents: Read and write`（fine-grained）或 `repo`（classic）。用完记得删除。

## 部署情况与隐私说明

| 项目 | 状态 |
| --- | --- |
| 仓库可见性 | 公开（Public） |
| GitHub Pages | 已开启，来源 `main` 分支根目录 |
| 站点网址 | <https://mchara520.github.io/YXB-intro/> |

**关于隐私**：仓库是公开的，所以**代码和网站所有人都能看到**。如果将来想要"只有自己能看"，有三条路：

1. 把仓库改回 **私有** 并关闭 Pages —— 代码有备份，但线上网址失效
2. 升级 **GitHub Pro** —— 私有仓库也能发布 Pages（带访问控制）
3. 迁移到 **Cloudflare Pages + Access** 或 **Netlify**（免费版支持密码保护）

> 曾经的坑：本仓库的 Pages 一度被一个已失效的自定义域名 `ayaka47.leleosd.top` 占用，
> 导致所有请求 502。已通过 Pages API 执行 `PUT {"cname":null}` 清除，站点恢复正常。
> 同样的问题也曾影响 <https://mchara520.github.io/>，一并修复。

## 字体授权提醒

`字魂流氓兔体` 的字体内嵌名称标注为「商用需授权」。本站目前是**公开**状态，请确认授权范围；
个人非商用展示通常没有问题。

## 背景插画

插画作者：@EE来步（如用于公开发布，请确认署名与授权要求）。

## 修改内容

所有文字都在 `index.html` 里，按注释分区即可直接改：

| 想改什么 | 在哪里 |
| --- | --- |
| 名字、身份一句话 | `<h1 class="name">` / `<p class="role">` |
| 自我介绍、签名句 | 「关于我」区块的 `.lead` 与 `.quote` |
| 生日、性别、职业等 | 「基本资料」区块的 `.fact` |
| 兴趣爱好标签 | 「喜欢的东西」区块的 `.chip` |
| 能力条百分比 | `style="--w:92%"` 里的数字 |
| 联系方式 | `mailto:` 链接与按钮文字 |

## 响应式与滚动行为

| 项目 | 手机端（≤900px） | 电脑端（≥901px） |
| --- | --- | --- |
| 布局 | 插画在上，卡片在下，单列 | 卡片横向铺满，内容自适应 1~3 栏 |
| 滚动方式 | **整页自然滚动**（方案②） | **卡片锁定一屏高度，卡片内部滚动**（方案③） |
| 滚动条位置 | 浏览器窗口右侧 | 卡片右内侧（细粉色滚动条） |
| 卡片边框 | 随内容一起滚动 | 始终完整贴合屏幕，构图固定 |
| 底部版权行 | 跟着内容走 | 固定在卡片底部，始终可见 |
| 回到顶部按钮 | 页面滚过 420px 后出现 | 隐藏（卡片自身可滚，不需要） |

电脑端分栏：≥1300px 为 3 栏，1061–1299px 为 2 栏，901–1060px 为 1 栏。
