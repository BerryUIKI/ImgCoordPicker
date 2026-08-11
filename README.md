# ImgCoordPicker 图片坐标拾取工具

> 🖱️ 图片坐标拾取工具 —— 为提示词 / AI 工作流而生

<p>
  <a href="https://github.com/BerryUIKI/ImgCoordPicker/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="License: MIT"></a>
  <a href="https://github.com/BerryUIKI/ImgCoordPicker"><img src="https://img.shields.io/badge/Platform-Web-darkgreen.svg" alt="Platform: Web"></a>
  <a href="https://github.com/BerryUIKI/ImgCoordPicker"><img src="https://img.shields.io/badge/Dependencies-Zero-brightgreen.svg" alt="Zero Dependencies"></a>
  <a href="https://berryuiki.github.io/ImgCoordPicker/"><img src="https://img.shields.io/badge/Live-Demo-orange.svg" alt="Live Demo"></a>
  <a href="https://github.com/BerryUIKI"><img src="https://img.shields.io/badge/Author-BerryUIKI-4f8cff.svg" alt="Author: BerryUIKI"></a>
</p>

一个轻量、零依赖的网页工具，用于从图片上拾取坐标点或框选区域，并输出**像素坐标**与**百分比坐标**，方便直接粘贴到 ComfyUI / Stable Diffusion 等提示词工具中使用。

单文件 HTML，浏览器直接打开即可运行，无需安装、无需构建、无需后端。

---

## 🚀 在线预览

👉 **[点此在线体验](https://berryuiki.github.io/ImgCoordPicker/)**（GitHub Pages 部署）

---

## ✨ 功能特性

- **🌐 多语言支持**：内置中文/English 切换，一键切换
- **🖱️ 自动模式**：单击 = 点选坐标，长按拖动 = 框选区域，无需切换工具
- **🖼️ 多图片工作流**：左侧缩略图面板，多图切换、独立标注，互不干扰
- **↩️ 撤销 / 重做**：`Ctrl+Z` / `Ctrl+Shift+Z`（`Ctrl+Y`），最多回溯 50 步
- **🎯 选中高亮**：点击标注即高亮，`Delete` 删除、`Ctrl+C` 复制坐标、`Esc` 取消
- **📝 画布内联编辑**：双击标注标签直接在原位置修改文字
- **📐 吸附辅助**：框选按住 `Shift` 可锁定水平/垂直/正方形；网格辅助线一键开关
- **🗂️ 面板分组**：标注列表可按「类型」或「文字」分组浏览
- **📤 多格式导出**：文本 / JSON / SVG / ComfyUI 区域 / COCO 五种格式输出
- **📥 导入数据**：一键导入 JSON 标注文件继续编辑
- **📐 双单位输出**：百分比 / 像素 + 百分比，自由切换
- **🔍 像素级放大镜**：悬停即放大 10×，精准定位
- **📝 文字标注**：每个点/框都能输入提示词或说明文字
- **📋 一键复制**：所有标注结果统一格式，直接粘贴使用
- **📐 尺寸自适应**：上传图片自动适应窗口并居中，支持 Ctrl+滚轮缩放
- **🎯 框选尺寸显示**：拖拽时实时显示选区 `宽 × 高`
- **📁 拖拽上传**：直接把图片拖进窗口即可加载

---

## 🛠️ 快速开始

### 方式一：直接打开（推荐）

下载 `index.html`，用浏览器（Chrome / Edge / Firefox）双击打开即可。

### 方式二：本地服务器

```bash
# 进入项目目录
cd ImgCoordPicker

# 使用 Python 启动本地服务器
python -m http.server 8080
```

然后访问 http://localhost:8080

---

## 🎯 使用方法

1. **加载图片**：点击「上传图片」或直接把图片拖进窗口
2. **多图片管理**：左侧缩略图面板点击切换图片，支持添加/删除图片
3. **点选**：单击图片任意位置，生成红色坐标点
4. **框选**：按住鼠标左键拖动，松开即框选区域（按住 `Shift` 可吸附锁定）
5. **输入文字**：双击标注标签直接在画布上编辑，或点击右侧列表输入框
6. **选择输出格式**：文本 / JSON / SVG / ComfyUI / COCO 自由切换
7. **复制结果**：点击「复制结果」一键复制全部标注
8. **导出/导入**：导出 JSON 存档，或导入已有 JSON 继续编辑

### 输出格式示例

百分比模式：

```
1. x=12.50%, y=34.20% : 按钮
2. x=45.00%, y=67.80% : 输入框
3. x=10.00%, y=20.00% to x=30.00%, y=40.00% : 图片区域
```

像素 + 百分比模式：

```
1. x=120px, y=340px (12.50%, 34.20%) : 按钮
2. x=450px, y=678px (45.00%, 67.80%) : 输入框
```

---

## ⌨️ 快捷键

| 操作 | 说明 |
|------|------|
| `Ctrl + 滚轮` | 缩放图片 |
| `⤢ 适应` 按钮 | 恢复自适应视图 |
| `Ctrl + Z` | 撤销上一步操作 |
| `Ctrl + Shift + Z` / `Ctrl + Y` | 重做（取消撤销） |
| `Delete` / `Backspace` | 删除当前选中的标注 |
| `Ctrl + C` | 复制选中标注的坐标 |
| `Esc` | 取消框选拖动 / 取消选中 |
| `Shift + 拖动` | 框选时吸附锁定（水平/垂直/正方形） |

---

## 🛠️ 技术说明

- **纯前端**：单文件 HTML + CSS + JavaScript，零依赖
- **Canvas + SVG**：Canvas 渲染图片，SVG 叠加标注
- **完全本地运行**：图片不会上传到任何服务器，隐私安全

---

## 📁 项目结构

```
ImgCoordPicker/
├── index.html      # 主程序（单文件）
├── README.md       # 项目说明
└── LICENSE         # MIT 许可证
```

---

## 🤝 贡献与支持

欢迎提交 [Issue](https://github.com/BerryUIKI/ImgCoordPicker/issues) 或 [Pull Request](https://github.com/BerryUIKI/ImgCoordPicker/pulls)！

如果你有任何改进建议或功能需求，请随时提出，或 Fork 本仓库进行开发。

---

## 👤 作者

**BerryUIKI**

- 🌐 GitHub: [@BerryUIKI](https://github.com/BerryUIKI)
- 📦 这个项目: [ImgCoordPicker](https://github.com/BerryUIKI/ImgCoordPicker)

如果你的项目也用到了这个工具，欢迎在下方留言反馈，或直接联系我。

---

## ⭐ Star 一下

如果这个工具对你有帮助，欢迎点个 **⭐ Star** 支持！你的支持是我持续更新的动力 💪

---

## 📄 许可证

[MIT](LICENSE) © [BerryUIKI](https://github.com/BerryUIKI)