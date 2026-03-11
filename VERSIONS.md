# 简历版本管理

## 📁 目录结构
```
resumes/
├── base/                              # 基础版本（完整经历）
│   ├── resume-base-2026-03-11-12-03.md    # v1.0 - 初始版本（整合 25 年总结）
│   ├── resume-base-2026-03-11-12-03.pdf   # ✅ PDF 版本（A4，2 页）
│   └── resume-base.md                     # 当前最新版（符号链接/工作文件）
├── versions/                          # 针对不同岗位的定制版本
│   ├── openclaw-integration-engineer-2026-03-11-12-03.md  # v1.0 - OpenClaw 岗位
│   ├── openclaw-integration-engineer-2026-03-11-12-03.pdf # ✅ PDF 版本（A4，2 页）
│   ├── openclaw-integration-engineer.md                     # 当前最新版（工作文件）
│   └── ...                            # 未来其他岗位版本
├── VERSIONS.md                        # 本文件 - 版本索引与变更日志
└── README.md                          # 岗位定制指南
```

---

## 📋 版本命名规范

### 格式
```
<岗位/类型>-YYYY-MM-DD-HH-MM.md
```

### 示例
- `resume-base-2026-03-11-12-03.md` - 基础版本，2026 年 3 月 11 日 12:03 创建
- `openclaw-integration-engineer-2026-03-11-12-03.md` - OpenClaw 岗位版，同时同刻
- `tech-lead-2026-03-12-09-00.md` - 技术负责人岗位，次日 9:00 创建

### 原则
1. **每次更新创建新文件** - 不在旧文件上修改
2. **时间戳精确到分钟** - 便于追溯和对比
3. **保留所有历史版本** - 不删除旧文件
4. **工作文件使用无时间戳名称** - 便于日常编辑

---

## 📝 版本索引

### 基础版本系列

| 版本 | 文件名 | 创建时间 | 格式 | 主要更新 |
|------|--------|----------|------|----------|
| v1.0 | `resume-base-2026-03-11-12-03.md` | 2026-03-11 12:03 | Markdown | 初始版本，整合 25 年工作总结与 26 年规划 |
| v1.0 | `resume-base-2026-03-11-12-03.pdf` | 2026-03-11 12:16 | PDF (A4) | ✅ 已导出，2 页以内 |

**v1.0 关键更新**:
- ✅ 补充 506 个测试用例验收、65 个 BUG/优化点关闭
- ✅ 增加西溪湿地试点验证（无 P0 级事故）
- ✅ 详细展开 3 次重大故障排查（业务耦合/监控缺失/缓存缺陷）
- ✅ 加入 2026 年度规划（全渠道生态、会员体系、数据中台、团队建设）
- ✅ 更新关键指标汇总表（新增质量管理、需求治理等维度）

---

### OpenClaw 自动化集成工程师岗位系列

| 版本 | 文件名 | 创建时间 | 格式 | 主要更新 |
|------|--------|----------|------|----------|
| v1.0 | `openclaw-integration-engineer-2026-03-11-12-03.md` | 2026-03-11 12:03 | Markdown | 初始版本，针对 OpenClaw 岗位定制 |
| v1.0 | `openclaw-integration-engineer-2026-03-11-12-03.pdf` | 2026-03-11 12:17 | PDF (A4) | ✅ 已导出，2 页以内 |

**v1.0 核心匹配点**:
- ✅ OpenClaw 数字员工系统实战经验
- ✅ Python 8 年 + 工程能力
- ✅ API 集成（飞书/Notion/阿里云/uniCloud）
- ✅ RAG 语义搜索（阿里云 embedding）
- ✅ Prompt Engineering 实战
- ✅ 自动化测试 + CI/CD 流程
- ✅ 3 次重大故障根因分析与解决
- ✅ 2026 年 AI 自动化方向规划

---

## 🎯 创建新版本流程

### 1. 编辑工作文件
```bash
# 编辑无时间戳的工作文件
vim resumes/base/resume-base.md
# 或
vim resumes/versions/<岗位>.md
```

### 2. 创建新版本（带时间戳）
```bash
# 基础版本
cp resumes/base/resume-base.md resumes/base/resume-base-$(date +%Y-%m-%d-%H-%M).md

# 定制版本
cp resumes/versions/openclaw-integration-engineer.md resumes/versions/openclaw-integration-engineer-$(date +%Y-%m-%d-%H-%M).md
```

### 3. 更新版本索引
在 `VERSIONS.md` 中记录：
- 版本号（v1.0, v1.1, v2.0 等）
- 文件名（带时间戳）
- 创建时间
- 主要更新内容

### 4. 更新 README.md（如需要）
如果岗位定制策略有调整，更新 README.md 中的指南。

---

## 📊 版本对比建议

### 使用 diff 工具
```bash
# 对比两个版本
diff resumes/base/resume-base-2026-03-11-12-03.md resumes/base/resume-base.md

# 使用 git diff（如果启用 git）
git diff resumes/base/resume-base-2026-03-11-12-03.md resumes/base/resume-base.md
```

### 关注点
- 新增/删除的经历
- 量化指标的变化
- 技能描述的调整
- 岗位匹配度的优化

---

## 💡 最佳实践

### 1. 版本命名
- ✅ `resume-base-2026-03-11-12-03.md` - 清晰明确
- ❌ `resume-base-v1.md` - 时间信息缺失
- ❌ `resume-base-final.md` - 永远有"最终版"
- ❌ `resume-base-最新.md` - 无法追溯

### 2. 更新频率
- **基础版本**：每次重大经历变化后更新（新项目、新技能、新成果）
- **定制版本**：每次投递前根据 JD 调整
- **时间戳**：精确到分钟，避免重复

### 3. 文件管理
- **工作文件**：无时间戳，便于日常编辑
- **历史版本**：带时间戳，只读不修改
- **定期清理**：保留近 6 个月版本，更早版本可归档

### 4. 投递追踪
建议用表格记录：

| 公司 | 岗位 | 简历版本 | 投递日期 | 状态 | 备注 |
|------|------|----------|----------|------|------|
| 示例公司 | OpenClaw 自动化集成工程师 | openclaw-integration-engineer-2026-03-11-12-03.md | 2026-03-11 | 已投递 | 内推 |

---

## 🔒 安全备份

### 本地备份
```bash
# 每周备份到外部存储
rsync -av resumes/ /mnt/backup/resumes/
```

### 云同步
```bash
# 使用 git 管理（推荐）
git add resumes/
git commit -m "Add resume version 2026-03-11-12-03"
git push origin main
```

### 敏感信息保护
- ⚠️ **不要**在简历中明文写入密码、密钥
- ⚠️ **不要**提交包含个人隐私的版本到公开仓库
- ✅ 使用脱敏版本对外投递

---

*最后更新：2026-03-11 12:04*  
*版本管理原则：每次更新创建新文件，保留完整历史轨迹*
