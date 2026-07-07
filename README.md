# Lazy Bird Portfolio

这是一个可直接部署到 GitHub Pages 的静态个人作品集网站。当前网站基于文件夹里的策划文档和视觉参考素材生成，核心主题是“慢慢创作，认真表达”。

## 文件说明

- `index.html`：页面结构。
- `styles.css`：视觉样式。
- `app.js`：作品筛选、项目详情弹窗、复制联系方式。
- `site-data.js`：个人信息、能力清单、关键词和项目案例。
- `assets/`：网页图片素材。
- `.nojekyll`：让 GitHub Pages 原样发布静态文件。
- `publish/`：干净发布目录，只包含 GitHub Pages 需要上传的文件。

## 本地预览

可以直接双击打开 `index.html`。如果希望用本地服务预览，在这个文件夹运行：

```powershell
python -m http.server 8080
```

然后打开：

```text
http://localhost:8080
```

## 发布到 GitHub Pages

建议上传 `publish/` 文件夹里的内容，不要把 Word 原稿和临时文件一起公开。

方式一：发布到个人主页仓库。

1. 在 GitHub 创建仓库，仓库名写成 `你的GitHub用户名.github.io`。
2. 把 `publish/` 文件夹里的全部内容上传到仓库根目录。
3. 等待 GitHub Pages 自动发布。
4. 访问 `https://你的GitHub用户名.github.io/`。

方式二：发布到普通仓库。

1. 在 GitHub 创建任意仓库，例如 `lazy-bird-portfolio`。
2. 把 `publish/` 文件夹里的全部内容上传到仓库根目录。
3. 进入仓库 `Settings` -> `Pages`。
4. `Build and deployment` 选择 `Deploy from a branch`。
5. 分支选择 `main`，目录选择 `/root`，保存。
6. 访问 GitHub Pages 页面给出的链接，通常是 `https://你的GitHub用户名.github.io/lazy-bird-portfolio/`。

## 更换图片

1. 把新图片放进 `assets/`。
2. 打开 `site-data.js`。
3. 找到对应项目的 `cover` 字段。
4. 改成新图片路径，例如：

```js
cover: "assets/new-project-cover.jpg"
```

首页大图在 `index.html` 里这一行：

```html
<img class="hero-cover" src="assets/site-cover.svg" ... />
```

把 `src` 改成新的图片路径即可。

## 后续生图风格

如果后续需要新增项目封面、角色动作或页面插画，建议使用 image 2，并保持这套调性：

- 雾紫背景、蓝绿海面或模块重点、橙色视觉焦点、奶油黄点缀。
- 粗黑描边、手绘卡通质感、轻微纸张纹理。
- 小鸟状态可以是趴着、发呆、慢慢飞、抱作品文件、拿画笔或坐在电脑前。
- 画面要松弛、有一点幽默，但不能幼稚，也不能变成商务科技风。

## 增加项目案例

打开 `site-data.js`，在 `projects` 数组里复制一整个项目对象，改成新项目内容。格式如下：

```js
{
  id: "new-project-id",
  title: "新项目标题",
  category: "品牌策划",
  year: "2026",
  role: "你负责的内容",
  cover: "assets/new-project-cover.jpg",
  summary: "项目一句话概述。",
  problem: "这个项目要解决的问题。",
  strategy: "你的创意策略或执行方法。",
  result: "最终成果或项目总结。",
  tags: ["标签一", "标签二", "标签三"]
}
```

`category` 可以写新的分类。页面会自动生成筛选按钮。

## 修改联系方式

打开 `site-data.js`，修改：

```js
email: "your-email@example.com",
wechat: "请替换为你的微信号",
resumeUrl: "#"
```

如果要放简历，把 PDF 放进 `assets/`，再把 `resumeUrl` 改成类似：

```js
resumeUrl: "assets/resume.pdf"
```
