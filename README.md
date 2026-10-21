# YuqueToMarkdown

将语雀导出的知识库（`.lakebook`）转换为保留目录层级与本地图片的 Markdown 压缩包。

## 解决的问题

语雀导出的 `.lakebook` 文件本质是一个 TAR 归档包，内部的 JSON 文档默认全量平铺，知识库的目录层级记录在 `$meta.json`（`book.tocYml`）中。

常规脚本如果只按标题简单重命名导出，容易产生以下问题：
- 目录层级丢失，所有文档被拍平在单个目录下；
- 目录容器节点（没有正文只有子页面的目录）被直接丢弃；
- 同名文档（如多次出现的“无标题文档”、“总结”）相互覆盖；
- 正文图片仍指向语雀在线 CDN，离线或图床失效后无法显示。

本工具在浏览器本地解析大纲树并重新组织输出：
- **保留完整目录结构**：根据大纲树递归创建多层文件夹；
- **图片离线化**：并发下载正文图片至本地 `assets/` 目录，文档内引用自动替换为对应深度的相对路径；
- **重名保护**：同级目录下的同名文件自动追加编号，避免覆盖；
- **目录索引 (MOC)**：为包含子文档的目录生成 `_index.md` 并附带子页面链接，便于在 Obsidian 等笔记软件中浏览；
- **代码与表格**：保留代码块语言标识（R、Python、Bash 等）与 Markdown 表格语法；
- **本地运行**：纯前端 JavaScript 处理，无需安装 Node.js 或 Python 环境，不向服务器上传任何文件。

## 使用方法

### 方式 1：本地直接打开
直接用浏览器双击打开 `index.html`，把 `.lakebook` 文件拖入页面，转换完成后会自动打包并触发浏览器下载。

### 方式 2：在线使用 (GitHub Pages)
在仓库的 **Settings -> Pages** 中，将 Source 选为 `Deploy from a branch`（分支 `main`，目录 `/(root)`），即可通过 GitHub Pages 在线运行。

## 选项说明

页面提供以下三个轻量开关（默认均开启）：
- **离线图片至 assets/**：抓取正文中的图片并写入压缩包的 `assets/` 目录，将远程链接替换为相对路径；
- **目录索引 (_index.md)**：为目录节点生成索引文件；
- **YAML Frontmatter**：在每篇 Markdown 顶部添加包含标题等元数据的 YAML 标头。

## 依赖开源组件

- [Turndown](https://github.com/mixmark-io/turndown) - HTML 转 Markdown
- [turndown-plugin-gfm](https://github.com/laurent22/turndown-plugin-gfm) - GFM 表格插件
- [js-untar](https://github.com/antelle/js-untar) - 浏览器 TAR 解包
- [js-yaml](https://github.com/nodeca/js-yaml) - YAML 解析
- [JSZip](https://github.com/Stuk/jszip) - 浏览器端 ZIP 压缩
- [FileSaver.js](https://github.com/eligrey/FileSaver.js/) - 文件下载触发

## 开源协议

MIT License
