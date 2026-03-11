# 简历版本管理规则

## 📋 核心规则（2026-03-11 13:06 更新）

### 1. 文件命名
- **不带时间戳** = 最新版本（工作文件）
  - `resume-base.md` - 基础版本最新工作文件
  - `openclaw-integration-engineer.md` - OpenClaw 岗位最新工作文件
- **带时间戳** = 历史存档（仅 MD）
  - `resume-base-2026-03-11-13-06.md` - 历史存档副本
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

### 4. HTML 规范（重要！）

#### 4.1 页数控制
- **严格控制在 2 页 A4 纸**
- 如果超过 2 页，继续压缩参数

#### 4.2 压缩参数（极限版）
- **页边距**: 8mm（上下）, 10mm（左右）
- **字号**: 9.5pt（正文）, 8.5pt（code）
- **行距**: 1.3
- **段落间距**: 3px
- **列表间距**: 3px
- **标题间距**: 10px/8px/6px

#### 4.3 URL 完整显示（❗极其重要）
**所有超链接必须在打印为 PDF 时显示完整 URL 地址**

**实现方式**:
```python
import re

def url_to_link(match):
    url = match.group(0)
    return f'<a href="{url}">{url}</a>'

html_content = markdown.markdown(md_content, extensions=['tables', 'fenced_code'])
html_content = re.sub(r'https?://[^\s\)">]+', url_to_link, html_content)
```

**效果对比**:
- ✅ **正确**: `<a href="https://...">https://...</a>` - 链接文字和地址相同
- ❌ **错误**: `<a href="https://...">点击这里</a>` - 看不到 URL

**CSS 样式**:
```css
a { 
    color: #3498db; 
    text-decoration: none; 
    word-break: break-all;  /* 防止长 URL 溢出 */
}
@media print { 
    a { 
        text-decoration: none !important; 
        color: #2c3e50 !important;  /* 打印时显示深色 */
    }
}
```

#### 4.4 排版风格
- **蓝色主题**: #3498db
- **左侧边框**: h2 标题 2px 蓝色边框
- **打印优化**: 移除渐变背景

### 5. 打印 PDF
- 在浏览器中打开 HTML（推荐 Chrome）
- Ctrl+P（或 Cmd+P）
- 选择"另存为 PDF"
- 纸张大小：A4
- 页边距：默认（CSS 中已设置 8mm/10mm）
- **确认页数：必须刚好 2 页**
- **确认 URL：所有链接都显示完整地址**

### 6. 文档维护
- **README.md**: 项目说明和使用指南
- **VERSIONS.md**: 版本管理规则和历史记录
- **及时更新**: 每次修改后同步更新这两个文件
- **禁止**: 文件末尾不要有【最后更新】之类的提示

---

## 📁 目录结构

```
resumes/
├── base/
│   ├── resume-base.md                     # ✅ 最新版本（工作文件）
│   ├── resume-base.html                   # ✅ 最新版本 HTML（2 页）
│   └── resume-base-2026-03-11-13-06.md    # 📦 历史存档（仅 MD）
├── versions/
│   ├── openclaw-integration-engineer.md          # ✅ 最新版本
│   ├── openclaw-integration-engineer.html        # ✅ 最新版本 HTML（2 页）
│   └── openclaw-integration-engineer-2026-03-11-13-06.md  # 📦 历史存档
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

2. **生成 HTML（URL 完整显示）**
```python
import markdown
import re

def url_to_link(match):
    url = match.group(0)
    return f'<a href="{url}">{url}</a>'

html_content = markdown.markdown(md_content, extensions=['tables', 'fenced_code'])
html_content = re.sub(r'https?://[^\s\)">]+', url_to_link, html_content)
```

3. **创建存档**
```bash
TIMESTAMP=$(date +%Y-%m-%d-%H-%M)
cp resumes/base/resume-base.md resumes/base/resume-base-$TIMESTAMP.md
rm -f resumes/base/resume-base-*.html  # 删除历史 HTML
```

4. **更新文档**
```bash
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
| v1.0 | `resume-base-2026-03-11-13-06.md` | 2026-03-11 13:06 | 极限压缩页边距到 8mm/10mm，确保 URL 完整显示 |
| v0.3 | `resume-base-2026-03-11-13-01.md` | 2026-03-11 13:01 | 压缩到 9.5pt/1.35 行距/12mm 页边距 |
| v0.2 | `resume-base-2026-03-11-12-57.md` | 2026-03-11 12:57 | URL 完整显示修正 |
| v0.1 | `resume-base-2026-03-11-12-49.md` | 2026-03-11 12:49 | 专业简历排版优化 |
| v0.0 | `resume-base-2026-03-11-12-36.md` | 2026-03-11 12:36 | 初始版本（删除历史版本重新开始） |

---

## 💡 注意事项

### URL 显示（❗最重要）
- ✅ **必须**: 所有超链接显示完整 URL 地址
- ✅ **实现**: Python 正则替换，链接文字=URL 地址
- ✅ **打印**: PDF 中可以看到完整 https://... 地址
- ❌ **禁止**: 只显示链接文字不显示 URL

### 页数控制
- **目标**: 严格 2 页 A4
- **如果超过**: 
  - 减小页边距（最低 8mm）
  - 缩小字号（最低 9pt）
  - 减小行距（最低 1.2）
  - 删减次要内容

### 存档频率
- **基础版本**: 每次修改后都存档
- **定制版本**: 根据岗位 JD 调整时存档
- **时间戳**: 精确到分钟

### 文档更新
- **README.md**: 项目说明，包含可用版本和使用方法
- **VERSIONS.md**: 版本管理规则和历史记录
- **及时性**: 每次修改后必须同步更新

---

*版本管理规则制定：2026-03-11*  
*最后更新：2026-03-11 13:06（URL 完整显示 + 极限压缩）*
