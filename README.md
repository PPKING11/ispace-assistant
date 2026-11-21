# iSpace 助手

<p align="center">
  <img src="https://img.shields.io/badge/Package-v7-blue?style=flat-square" alt="Package v7"/>
  <img src="https://img.shields.io/badge/Platform-Windows-0078D4?style=flat-square" alt="Windows"/>
  <img src="https://img.shields.io/badge/Browser-Chrome-orange?style=flat-square&logo=googlechrome" alt="Chrome"/>
  <img src="https://img.shields.io/badge/Node.js-22.13%2B-green?style=flat-square&logo=nodedotjs" alt="Node.js 22.13+"/>
  <img src="https://img.shields.io/badge/Entry-Codex-purple?style=flat-square" alt="Codex"/>
  <img src="https://img.shields.io/badge/Sites-Owner--only-lightgrey?style=flat-square" alt="Owner-only Sites"/>
</p>

> 在 Codex 聊天里查自己的 iSpace 课程、作业和课件，接收截止提醒，按年级、学期和课程把课件存到 Windows。

**安装包** [下载 v7 ZIP](ispace-assistant-v7.zip?raw=true) · [SHA-256](ispace-assistant-v7.zip.sha256)

---

## 验收摘要

| 项目 | 验收目标 | 结果 |
|------|----------|------|
| 私人站点 | 从安装包独立解压、构建并启动 | ✅ 已通过 |
| 首次设置 | 打开表单、保存选项、回读配置 | ✅ 已通过 |
| 课件和日报 | 下载一份真实课件并收到定时下载日报 | ✅ 已实测 |

---

## 目录

- [文件结构](#文件结构)
- [部署与运行](#部署与运行)
- [核心功能](#核心功能)
- [配置与默认值](#配置与默认值)
- [完整验收结果](#完整验收结果)
- [设计说明](#设计说明)

---

## 文件结构

```text
iSpace-assistant-v7/
├── README.md              # 快速入口和部署说明索引
├── ispace-site/           # 私人站点源码和部署手册
├── ispace-assistant/      # 首次设置、作业提醒和聊天交接
├── ispace-course-local/  # Windows 文件助手和 Chrome 课件扩展
├── ispace-attendance-local/ # Chrome 签到扩展
└── SHA256SUMS             # 包内文件校验清单
```

---

## 部署与运行

> **环境要求** Windows、Chrome、Git、Node.js 22.13 或更新版本、能使用 Sites 的桌面版 Codex 账号，以及学校为本人开通的 iSpace 服务令牌。

1. **打开助手项目。** 解压完整安装包，在桌面版 Codex 把 `ispace-assistant` 打开为本地项目。将一站式设置说明（包内 `ispace-assistant/README.md`）里的配置指令发到新聊天。
2. **部署私人站点。** 用 `ispace-site` 建立仅本人可访问的站点、设置运行参数并发布。学校令牌填入 Sites 设置的 Secret 字段。 私人站点部署（包内 `ispace-site/README.md`）
3. **连接学校账号。** 在自己站点的 `/setup` 选择课程，完成首次同步，再连接该站点生成的 Codex 插件。
4. **完成首次设置。** 填姓名和学号，确认是否下载到电脑、检查间隔和作业提醒。助手登记主副聊天、应用后台巡检并核对状态。
5. **试下载并核对。** 开启本机下载时，安装 Windows 文件助手和 Chrome 课件扩展，配对站点后试下载一份课件。 本机下载组件（包内 `ispace-course-local/README.md`）

### 查看配置进度

在解压目录运行以下命令，再回到聊天试问「查一下我最近的作业」。

```powershell
cd ispace-assistant
node --no-warnings onboarding.mjs check
```

---

## 核心功能

### 1. 课程与资料

查本人课程、作业要求、截止和提交状态、已公布成绩及考试安排。可以打开课件、搜索已收录的附件正文。学校已发布可查的名单时，可凭姓名和学号定位自己的小组、考场和座位。

### 2. 作业与提醒

发现新作业后提醒，按题目和课件辅助规划、起草和核对。小组作业确认选题和人数后再拟定分工。正式提交前核对作业、文件版本和已有提交，并对具体文件和作业收取确认。

### 3. 文件下载与归档

Chrome 检查和下载新课件，Windows 文件助手按年级、学期和课程归档。下载日报列出新增、更新、缺失和跳过的文件。 下载扩展说明（包内 `ispace-course-local/README.md`）

### 4. 主副助手与换班

主助手负责聊天和汇总，副助手处理专项任务，后台负责巡检。换班会移交任务及文件，核对旧聊天的定时与置顶。旧聊天记录默认保留。 后台巡检与提醒（包内 `ispace-assistant/AUTOMATION.md`）

---

## 配置与默认值

| 配置 | 默认值或行为 |
|------|--------------|
| 本机下载 | 开启，可在首次设置关闭 |
| 下载目录 | 优先沿用已配对的目录，首次使用桌面的 `Course` |
| 课件检查间隔 | Chrome 打开时每 15 分钟检查一次 |
| 作业巡检 | 北京时间 08:10、20:10 |
| 截止提醒 | 截止前 12 小时内的首次巡检提醒一次 |
| 下载日报 | 默认北京时间 20:10，错过时可次日早上补查 |
| 主助手与副助手 | GPT‑6.2 Sol / High |
| 后台巡检 | GPT‑6.1 Terra / High |

---

## 完整验收结果

| 验收范围 | 已验证内容 | 状态 |
|----------|------------|------|
| 站点运行 | 独立解压后的依赖安装、类型检查、构建和本地启动 | ✅ 已通过 |
| 首次设置 | 保存选项、关闭下载后完成主副聊天登记 | ✅ 已通过 |
| 课件归档 | 单份真实课件保存、定时日报送达 | ✅ 已实测 |
| 提交与回执 | 提交前复核、防覆盖和回执归档 | 模拟测试通过，真实提交待验收 |
| 自动下载 | Chrome 整批自动下载 | 待完整验收 |
| 签到扩展 | 可从学校签到活动页由本人手动发起 | 待真实场次验收 |

---

## 设计说明

- 私人 Sites 用部署者自己的学校账号读取课程。学校服务令牌只填在 Sites 设置中。
- 姓名、学号、助手偏好和聊天进度保存在本机。每位使用者配置自己的私人站点和归档目录。
- Chrome 签到扩展从本人主动打开的学校活动读取场次。到场确认、口令、扫码等按学校页面操作。 签到扩展说明（包内 `ispace-attendance-local/README.md`）
