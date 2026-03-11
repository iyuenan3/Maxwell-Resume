# 简历版本管理规则

## 📋 核心规则

### 1. 文件命名
- **不带时间戳** = 最新版本（工作文件）
  - `resume-base.md` - 基础版本最新工作文件
  - `openclaw-integration-engineer.md` - OpenClaw 岗位最新工作文件
- **带时间戳** = 历史存档（仅 MD）
  - `resume-base-2026-03-11-12-36.md` - 历史存档副本
  - 格式：`YYYY-MM-DD-HH-MM`

### 2. 文件类型管理
| 文件类型 | 最新版本 | 历史版本 |
|----------|----------|----------|
| Markdown (.md) | ✅ 保留 | ✅ 保留（存档） |
| HTML (.html) | ✅ 仅最新版本 | ❌ 不保留 |
| PDF (.pdf) | ❌ 用户自行打印 | ❌ 不保留 |

### 3. 存档规则
- **每次修改基础版本 MD 后** → 立即复制一份带时间戳的存档
- **历史版本只保留 MD** → 删除 HTML
- **最新版本保留 MD + HTML** → 便于浏览器预览和打印

### 4. HTML 规范
- **严格控制在 2 页 A4 纸**
- **页边距**: 20mm（上下）, 18mm（左右）
- **字号**: 10.5pt（正文）
- **行距**: 1.5
- **所有超链接显示完整地址**（便于 PDF 查看）
- **排版风格**: 专业简历风格
  - 蓝色主题色（#3498db）
  - 左侧边框强调章节
  - 渐变背景突出标题
  - 清晰的层级结构

### 5. 打印 PDF
- 在浏览器中打开 HTML
- Ctrl+P（或 Cmd+P）
- 选择"另存为 PDF"
- 纸张大小：A4
- 页边距：默认（CSS 中已设置）
- 确认页数为 2 页

### 6. 文档维护
- **README.md**: 项目说明和使用指南
- **VERSIONS.md**: 版本管理规则和历史记录
- **及时更新**: 每次修改后同步更新这两个文件

---

## 📁 目录结构

```
resumes/
├── base/
│   ├── resume-base.md                     # ✅ 最新版本（工作文件）
│   ├── resume-base.html                   # ✅ 最新版本 HTML
│   └── resume-base-2026-03-11-12-36.md    # 📦 历史存档（仅 MD）
├── versions/
│   ├── openclaw-integration-engineer.md          # ✅ 最新版本（工作文件）
│   ├── openclaw-integration-engineer.html        # ✅ 最新版本 HTML
│   └── openclaw-integration-engineer-2026-03-11-12-36.md  # 📦 历史存档
├── README.md
└── VERSIONS.md（本文件）
```

---

## 🎯 工作流程

### 修改简历时

1. **编辑工作文件**
```bash
vim resumes/base/resume-base.md
# 或
vim resumes/versions/openclaw-integration-engineer.md
```

2. **生成 HTML**
```bash
# 使用 Python 脚本生成 HTML
python3 generate-html.py
```

3. **创建存档**
```bash
TIMESTAMP=$(date +%Y-%m-%d-%H-%M)
cp resumes/base/resume-base.md resumes/base/resume-base-$TIMESTAMP.md
rm -f resumes/base/resume-base-*.html  # 删除历史 HTML
```

4. **更新文档**
```bash
# 更新 README.md 和 VERSIONS.md
vim resumes/README.md
vim resumes/VERSIONS.md
```

5. **推送到 GitHub**
```bash
cd resumes
git add .
git commit -m "Update: 修改内容说明"
git push origin main
```

---

## 📊 版本历史

| 版本 | 文件名 | 创建时间 | 主要修改 |
|------|--------|----------|----------|
| v1.0 | `resume-base-2026-03-11-12-36.md` | 2026-03-11 12:36 | 初始版本（删除关键指标汇总和岗位匹配度说明，统一超链接格式） |

---

## 💡 注意事项

### 超链接格式
- ✅ **正确**: `https://github.com/iyuenan3/k8s-om`
- ❌ **错误**: `[k8s-om](github.com/iyuenan3/k8s-om)`
- **原因**: PDF 中需要看到完整链接地址

### 页数控制
- 如果超过 2 页，可以：
  - 删减次要内容
  - 缩小字号（不低于 10pt）
  - 调整行距（不低于 1.4）
  - 合并相似条目

### 存档频率
- **基础版本**: 每次修改后都存档
- **定制版本**: 根据岗位 JD 调整时存档
- **时间戳**: 精确到分钟

### 文档更新
- **README.md**: 项目说明，包含可用版本和使用方法
- **VERSIONS.md**: 版本管理规则和历史记录
- **及时性**: 每次修改后必须同步更新这两个文件

---

*版本管理规则制定：2026-03-11*
