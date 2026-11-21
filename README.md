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

**安装包** [下载 v7 ZIP](https://raw.githubusercontent.com/PPKING11/ispace-assistant/main/ispace-assistant-v7.zip) · [SHA-256](ispace-assistant-v7.zip.sha256)

---

## 安装提示词

在桌面版 Codex 的新聊天里复制发送下面整段，可以从下载开始。

```text
请帮我在这台 Windows 电脑上下载并配置 iSpace 助手 v7。安装包直链如下。
https://raw.githubusercontent.com/PPKING11/ispace-assistant/main/ispace-assistant-v7.zip

请在我的「下载」目录创建 iSpace-assistant-v7 文件夹，下载 ZIP 并解压到该目录，保留解压后的目录结构。若已经有一份已核对的安装，请复用它。

将解压后的 ispace-assistant 文件夹添加为桌面版 Codex 的本地项目。使用可用的项目与聊天操作，在此项目中创建或复用主聊天，命名为「ispace助手」，打开并置顶它。已有主聊天时继续使用；如果这次聊天已在该项目里，可以直接把它设为主聊天。请在主聊天接续安装，阅读 ispace-assistant/README.md 和同级 ispace-site/README.md。

如果当前客户端无法添加本地项目或置顶，请给出准确的文件夹路径，告诉我在侧栏选择「添加项目」或在主聊天菜单选择「置顶」，完成后继续安装。

请用我自己的账号建立仅我本人可访问的私人 Sites，连接我的 iSpace 课程，完成首次同步并打开首次设置窗口。按我选的设置配置作业提醒和所需的本机组件。

需要学校登录、填写 iSpace 服务令牌或确认 Chrome 权限时，请告诉我具体在哪个页面操作，等我完成后继续。学校令牌由我填写到 Sites 设置的 Secret 字段。

首次设置保存后，在同一项目创建或复用后台副聊天「默默工作的后台员工」，按包内 ispace-assistant/README.md 登记主副聊天。读取 ispace-assistant/AUTOMATION.md，在我的账号里按当前安装目录核对已有配置，只创建或复用一项项目级定时「ispace助手｜后台检查与交接」。已有任务就更新原任务。侧栏中每次运行留下的同名聊天属于运行历史。把下面的换班步骤写进这项定时的提示词，连同包内 AUTOMATION.md 的巡检流程一起执行。每次巡检从本项目的 state.json 读取当前主聊天，向它发送已开启的提醒。

换班时，按本项目 WORKFLOW.md 的门槛和安全条件核对主副聊天。先处理已有交接。有待接续的工作且运行时允许创建时，按交接编号在同一项目新建一位候选，复用已登记候选。候选核对任务、负责人、文件版本和下一步并确认接班，随后才切换负责人。即使当轮未到作业巡检时间，也继续处理已有交接。

切换后按账本名称给新旧聊天改名。主聊天换班时，通过桌面版 Codex 的侧栏操作置顶新主聊天、取消旧主聊天置顶，并回读确认。按旧聊天 ID 暂停并核对它专属的 iSpace 定时，项目级巡检保留同一项。按我的偏好保留或归档旧聊天，首次默认保留。核对以上结果后，才在运行时登记交接完成。客户端缺少所需操作时，保留同一交接编号，把待办发给当前主聊天，后续继续核对。

默认每天北京时间 08:10 和 20:10 运行，后台模型为 GPT‑6.1 Terra / High。请核对任务已启用，并回读下次运行时间和模型。本机任务需要电脑和 Codex 能运行。如果当前客户端无法创建聊天或定时任务，请指出缺哪一步、到哪里操作，完成后继续。

最后请查一次我最近的作业，确认课程同步可用，并汇报本地项目、主聊天置顶、后台聊天和定时任务的实际状态。如果我开启了本机下载，再试下载一份课件并告诉我保存路径。

如果当前聊天无法下载文件到这台电脑，请给我上面的直链，并指出解压后在桌面版 Codex 里要打开的 ispace-assistant 文件夹。
```

---

## 验收摘要

| 项目 | 验收目标 | 结果 |
|------|----------|------|
| 私人站点 | 从安装包独立解压、构建并启动 | ✅ 已通过 |
| 首次设置 | 打开表单、保存选项、回读配置 | ✅ 已通过 |
| 课件和日报 | 下载一份真实课件并收到定时下载日报 | ✅ 已实测 |

---

## 目录

- [安装提示词](#安装提示词)
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

主助手负责聊天和汇总，副助手处理专项任务。一个本地项目只需一项「ispace助手｜后台检查与交接」。Codex 会为独立定时的每次运行创建一个聊天。在定时任务页可核对实际启用的任务。

主助手满 40 轮或 7 天、副助手满 25 轮或 3 天时，在有工作可接续且到达安全交接点后换班。接班聊天确认任务和文件后才接管。主聊天换班后置顶新聊天，取消旧聊天置顶，并核对旧聊天专属的 iSpace 定时。项目级巡检沿用原安排。旧聊天记录默认保留，也可按本人偏好归档。 后台巡检与提醒（包内 `ispace-assistant/AUTOMATION.md`）

已安装 v7 的使用者可以把安装提示词中从「首次设置保存后」开始的三段发给现有主聊天，请它更新并回读同一项巡检的提示词。

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
