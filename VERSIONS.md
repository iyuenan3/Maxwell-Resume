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
| PDF (.pdf) | ❌ 不生成 | ❌ 不保留 |

### 3. 存档规则
- **每次修改基础版本 MD 后** → 立即复制一份带时间戳的存档
- **历史版本只保留 MD** → 删除 HTML 和 PDF
- **最新版本保留 MD + HTML** → 便于浏览器预览和打印

### 4. HTML 规范
- **严格控制在 2 页 A4 纸**
- **页边距**: 15mm
- **字号**: 10.5pt（正文）
- **行距**: 1.4
- **所有超链接显示完整地址**（便于 PDF 查看）
  - ✅ `https://github.com/iyuenan3/k8s-om`
  - ❌ `[k8s-om](github.com/iyuenan3/k8s-om)`

### 5. 打印 PDF
- 在浏览器中打开 HTML
- Ctrl+P（或 Cmd+P）
- 选择"另存为 PDF"
- 纸张大小：A4
- 页边距：默认（15mm 已在 CSS 中设置）
- 确认页数为 2 页

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
# 删除历史 HTML（如果有）
rm -f resumes/base/resume-base-*.html
```

4. **推送到 GitHub**
```bash
cd resumes
git add .
git commit -m "Update: 修改内容说明"
git push origin main
```

---

## 📊 版本追踪

建议在表格中记录：

| 版本 | 文件名 | 创建时间 | 主要修改 |
|------|--------|----------|----------|
| v1.0 | `resume-base-2026-03-11-12-36.md` | 2026-03-11 12:36 | 初始版本（删除关键指标汇总和岗位匹配度说明） |

---

## 💡 注意事项

### 超链接格式
- ✅ **正确**: `LinkedIn: https://linkedin.com/in/iyuenan3`
- ❌ **错误**: `[LinkedIn](linkedin.com/in/iyuenan3)`
- **原因**: PDF 中需要看到完整链接地址

### 页数控制
- 如果超过 2 页，可以：
  - 删减次要内容
  - 缩小字号（不低于 10pt）
  - 调整行距（不低于 1.3）
  - 合并相似条目

### 存档频率
- **基础版本**: 每次修改后都存档
- **定制版本**: 根据岗位 JD 调整时存档
- **时间戳**: 精确到分钟

---

*最后更新：2026-03-11 12:36*  
*规则制定：Maxwell Li*
