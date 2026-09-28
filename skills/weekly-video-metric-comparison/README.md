# 视频指标对比

`weekly-video-metric-comparison` 用于补齐周度视频广告表格的指标区及绿色标记。

[返回视频优化总入口](../../README.md) · [查看完整规则](SKILL.md) · [在线制作流程](https://judebrisbylg-matthew.github.io/video-optimization/)

## 用途

映射花费、CPC、点击率、转化率、ACOS、5秒观看率、完播率的当前值。花费只展示；其余六项按确认的父ASIN基准设置条件格式。此 Skill 不进行视觉诊断、不填写优化结论。

## 使用步骤

1. 提交最新工作簿并说明目标日期，仅处理第一张工作表。
2. 按“分组表头＋指标名”识别数据来源和基准，确认期间一致。
3. 用公式显示当前值，设置六项标绿规则，不输出涨跌幅。
4. 检查数值、公式和标绿范围，保存新文件，不覆盖原件。
5. 需要分析图片与填写结论时，再使用 [视觉分析 Skill](../weekly-video-metric-comparison-2/)。

## 标绿规则

| 指标 | 条件 |
| --- | --- |
| CPC | 当前值 ≤ 基准 |
| 点击率、转化率、5秒观看率、完播率 | 当前值 > 基准 |
| ACOS | 当前值 < 基准 |
| 花费 | 不标绿 |

缺失、文本或错误值不应标绿。当前规则以半年字段为参考；近30天或近90天周表必须先确认对应口径。

## 安装

在 Codex 中发送：

```text
请使用 $skill-installer 安装：
https://github.com/judebrisbylg-matthew/video-optimization/tree/main/skills/weekly-video-metric-comparison
```

手动安装时，将本目录完整复制到 `~/.agents/skills/` 或项目 `.agents/skills/`。保留 `references/`。已有同名目录先备份，不直接覆盖。需要宿主具备 `spreadsheets:Spreadsheets` 依赖，详见[安装总说明](../../README.md#安装方法)。

## 使用示例

```text
使用 $weekly-video-metric-comparison，只补充第一张表中【日期】对应行的指标与绿色标记。先核对来源和基准期间，保留其他内容，输出新的 XLSX。
```
