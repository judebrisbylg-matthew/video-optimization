# 视频优化

每周视频广告分析的统一入口：先补齐指标与绿色标记，再结合运营备注、当前截图和优秀参考图，形成有依据、可执行的优化建议。

## 三个入口

| 入口 | 用途 |
| --- | --- |
| [① 视频指标对比 Skill](skills/weekly-video-metric-comparison/) | 补齐花费、CPC、点击率、转化率、ACOS、5秒观看率、完播率，并按基准标绿。 |
| [② 视频视觉分析 Skill](skills/weekly-video-metric-comparison-2/) | 填写数据分析原因、数据分析结论、视觉分析原因、视觉执行结论。 |
| [③ 在线查看制作流程](https://judebrisbylg-matthew.github.io/video-optimization/) | 点击查看完整流程、优化判断、填写示例和交付检查；可切换三种页面样式。 |

也可以直接查看 [HTML 源文件](docs/index.html)，下载到本地用浏览器打开。页面仅用于参考，不会自动读取或修改表格。

## 每周使用步骤

1. **人工准备**：提交最新 XLSX；补充每行当前视频前5秒截图、对应优秀素材截图、运营备注，并说明要分析的日期。
2. **确认范围**：只处理第一张工作表中指定日期的业务行；按实际多行表头识别字段，不固定套用列字母。
3. **指标对比**：缺少指标或标绿时，使用 Skill 1。已有内容完整时跳过，不重复覆盖。
4. **数据与视觉分析**：使用 Skill 2，依次核对运营备注、当前图片、对应参考图和指标。
5. **检查并交付**：保存新的 XLSX，检查修改范围、图片、公式和文字显示，保留原文件与其他日期内容。

## 安装方法

这两个目录是独立的 Skill，不是双击运行的软件。安装前，你的 Codex 环境需要具备本地文件访问、XLSX 编辑、图片读取和工作簿验证能力。两个 Skill 均依赖宿主提供的 `spreadsheets:Spreadsheets`；本仓库不打包该依赖，也不保证其他工具环境直接兼容。

### 方法一：让 Codex 安装（推荐）

在提供 `$skill-installer` 的 Codex 环境中，复制以下文字发送：

```text
请使用 $skill-installer，从 GitHub 仓库 judebrisbylg-matthew/video-optimization 安装以下两个技能：
skills/weekly-video-metric-comparison
skills/weekly-video-metric-comparison-2
如果已存在同名技能，请先提示我，不要直接覆盖。
```

也可以单独提供目录链接：

- 指标对比：https://github.com/judebrisbylg-matthew/video-optimization/tree/main/skills/weekly-video-metric-comparison
- 视觉分析：https://github.com/judebrisbylg-matthew/video-optimization/tree/main/skills/weekly-video-metric-comparison-2

### 方法二：手动安装

1. 点击仓库的 **Code → Download ZIP**，解压文件。
2. 将 `skills/` 下的两个完整目录复制到用户级 `~/.agents/skills/`，或项目级 `.agents/skills/`。Windows 用户级路径为 `%USERPROFILE%\.agents\skills\`。
3. 保留 `SKILL.md`、`references/` 以及已有的 `agents/`，不要只复制一份 Markdown。
4. 如有同名目录，先备份并确认更新方式，避免重复安装或覆盖旧版本。
5. 在技能列表中确认两个名称可见；如未出现，重启 Codex 后重试。

```text
.agents/skills/
├── weekly-video-metric-comparison/
│   ├── SKILL.md
│   └── references/comparison-rules.md
└── weekly-video-metric-comparison-2/
    ├── SKILL.md
    ├── references/analysis-rules.md
    └── agents/openai.yaml
```

安装目录与发现机制参考 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。不同版本的安装器可能使用不同目录，以安装结果为准，避免同一技能多处重复安装。

## 安装后如何使用

提交你的工作簿，并发送：

```text
只处理第一张工作表中【本周日期】的业务行。
先使用 $weekly-video-metric-comparison 补齐缺失的七项指标与绿色标记。
再使用 $weekly-video-metric-comparison-2 填写本次授权的分析字段。
原因写充分，执行结论写简约，按实际需要用（1）（2）分点，不硬凑三条。
换景只说明大概场景和色调，并保留必要的商品展示重点，不写门窗、桌椅等布景细节。
不需要优化的只写一条，说明哪些指标表现良好，并建议暂不优化、保留现有素材。
保护已有人工内容及其他日期；保存为新版本，不覆盖原文件。
```

如只想修改视觉执行结论，请明确指定，只修改该字段，不同时改写数据分析。

## 判断与写法边界

- **原因充分，执行简约**：原因说明指标与可见证据；执行只写必要动作。
- **标绿不等于绝对优秀**：标绿是相对已确认基准的结果。CPC、点击率和两项观看较好时优先保留素材，仍需核查商品真实性；转化问题另行排查。
- **不强制换景**：需要换景时写“纽约街头咖啡店场景，以灰米色、木色为主”这类方向，不指定微观布景；纽约仅是示例，不是统一模板。
- **不凭静态图推断全片**：两张截图不能证明全片节奏、转场和声音效果。
- **不跨款校色**：颜色、印花和版型以同SKC确认资料为准。
- **基准必须确认**：当前 Skill 1 原始规则以半年基准为例。遇到近30天、近90天或表头期间冲突时，先确认，不混用、不自行重算。
- **缺图不编造**：当前图缺失或归属不明时保留视觉内容并报告；可继续完成数据诊断。

## 版本说明

本次发布保留两个现有 Skill 本体，新增中文使用与安装说明，附上可视化流程 HTML。上方使用提示包含最新确认的简约表达偏好；HTML 中“建议写回 Skill”的部分仍是待同步项，不表示技能文件已完成更新。

仓库只包含技能与流程文档，不包含业务工作簿、商品素材、广告数据、账户凭据或个人路径。
