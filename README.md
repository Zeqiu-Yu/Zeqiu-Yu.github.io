# Zeqiu (Zach) Yu · Academic Homepage

网址：<https://zeqiu-yu.github.io>

基于 [al-folio](https://github.com/alshedivat/al-folio)（MIT License）搭建。每次 push 到 `main`，GitHub Actions 会自动构建，并发布到 `gh-pages` 分支。

## 第一次上线

0. 先把 GitHub 用户名改成 `Zeqiu-Yu`：**Settings → Account → Change username**。网址 `zeqiu-yu.github.io` 必须对应同名账号。
1. 在 GitHub 新建一个 **Public** 仓库，名字必须是 `Zeqiu-Yu.github.io`。不要勾选添加 README。
2. 打开仓库 **Settings → Actions → General → Workflow permissions**，选 **Read and write permissions**，然后 Save。
3. 在本文件夹里执行：

   ```bash
   git init -b main
   git add .
   git commit -m "Initial homepage"
   git remote add origin https://github.com/Zeqiu-Yu/Zeqiu-Yu.github.io.git
   git push -u origin main
   ```

   `.github/` 是隐藏文件夹，自动部署全靠它。所以请用 git 或 GitHub Desktop 上传，不要在网页上拖拽。

4. 到仓库的 **Actions** 页面，等 **Deploy site** 变成绿色，大约 3–6 分钟。完成后仓库里会多出一个 `gh-pages` 分支。
   - 如果第一次运行失败了，先确认第 2 步设置过，再点 **Re-run jobs**。
   - 期间如果看到一个 `pages-build-deployment` 失败，不用管，第 5 步做完就好了。
5. 打开 **Settings → Pages → Build and deployment**，Source 选 **Deploy from a branch**，Branch 选 `gh-pages` 和 `/ (root)`，然后 Save。
6. 等 1–2 分钟，打开 <https://zeqiu-yu.github.io>。

## 以后怎么更新

改完文件 push 到 `main`，网站几分钟内会自动更新。也可以直接在 GitHub 网页上点文件右上角的铅笔图标编辑，提交后同样会自动部署。

| 想改什么 | 改这个文件 |
| --- | --- |
| 简介、研究方向 | `_pages/about.md` |
| 头像 | `assets/img/prof_pic.jpg`（直接替换同名文件） |
| 新闻 | `_news/` 里新建一个 `.md` 文件，照着现有文件的格式写 |
| 论文 | `_bibliography/papers.bib` |
| CV 页面 | `_data/cv.yml` |
| 邮箱、Google Scholar、GitHub、LinkedIn | `_data/socials.yml` |
| 名字、网站描述、关键词 | `_config.yml` |
| 主题色 | `_sass/_themes.scss` 里的 `#1c5fa8`（al-folio 默认是紫色 `#b509ac`） |

### 论文条目常用字段（`papers.bib`）

- `selected = {true}`：显示在首页的 selected publications 里
- `abbr = {NeurIPS}`：左侧的会议标签，颜色在 `_data/venues.yml` 里配置
- `arxiv = {2501.01234}`、`pdf = {https://...}`、`code = {https://github.com/...}`、`website = {https://...}`：这些字段会变成论文下方的按钮
- `abstract = {...}`：会出现 Abs 按钮，点开显示摘要
- `preview = {xxx.png}`：论文缩略图，图片放在 `assets/img/publication_preview/`
- 共同一作：在姓后面加 `*`，例如 `Yuan*, R. and Yu*, Z.`

### 其他

- **在 CV 页放 PDF 下载**：把删掉电话和住址的 CV 放到 `assets/pdf/CV.pdf`，然后在 `_pages/cv.md` 的开头加一行 `cv_pdf: /assets/pdf/CV.pdf`。想让社交图标里也出现 CV 图标，把 `_data/socials.yml` 里的 `cv_pdf` 那行取消注释。
- **加回 Projects、Blog、Teaching 等页面**：从 [al-folio 原仓库](https://github.com/alshedivat/al-folio) 把 `_pages/` 里对应的文件拷回来，再修改其中的 `nav_order`。
- **本地预览（可选）**：装好 Docker 后运行 `docker compose up`，然后打开 <http://localhost:8080>。详见 al-folio 的 [安装文档](https://github.com/alshedivat/al-folio/blob/main/docs/INSTALL.md)。
