# Comparison Rules

## Canonical field map

Resolve every field by **group header + metric header**. Header dates and capitalization may vary; normalize whitespace and case, but do not collapse distinct groups that share names such as `CPC` or `转化率`.

| Output | Current-value source group | Source metric | Benchmark group | Benchmark metric | Green rule |
|---|---|---|---|---|---|
| 花费 / Spend | 近半年视频广告活动数据（数据源） | 花费 | — | — | Never green |
| CPC | 近半年视频广告活动数据（数据源） | CPC | 父ASIN近半年全部渠道投放数据 | CPC | current <= benchmark |
| 点击率 / CTR | 近半年视频广告活动数据（数据源） | CTR/点击率 | 父ASIN近半年视频投放数据 | 点击率 | current > benchmark |
| 转化率 / CVR | 近半年视频广告活动数据（数据源） | CVR/转化率 | 父ASIN近半年全部渠道投放数据 | 转化率 | current > benchmark |
| ACOS | 近半年视频广告活动数据（数据源） | ACoS/ACOS | 父ASIN近半年全部渠道投放数据 | ACOS | current < benchmark |
| 5秒观看率 | 近半年视频广告活动数据（数据源） | 5秒观看率 | 父ASIN近半年视频投放数据 | 5秒观看率/5秒观看率播率 | current > benchmark |
| 完播率 | 近半年视频广告活动数据（数据源） | 完播率 | 父ASIN近半年视频投放数据 | 完播率 | current > benchmark |

In the 2026-08-20 reference workbook, the canonical formulas were:

| Output column | Formula pattern | Benchmark reference |
|---|---|---|
| CP 花费 | `=O[row]` | none |
| CQ CPC | `=N[row]` | `BG[row]` |
| CR 点击率 | `=M[row]` | `AV[row]` |
| CS 转化率 | `=Q[row]` | `BI[row]` |
| CT ACOS | `=P[row]` | `BF[row]` |
| CU 5秒观看率 | `=V[row]` | `AX[row]` |
| CV 完播率 | `=W[row]` | `AY[row]` |

These letters are only a reference check. If a weekly workbook shifts columns, resolve the same compound headers and generate formulas from the resolved cells.

## Conditional formatting contract

Apply six independent expression rules to the real data range:

```text
CPC:      AND(ISNUMBER(current),ISNUMBER(benchmark),current<=benchmark)
CTR:      AND(ISNUMBER(current),ISNUMBER(benchmark),current>benchmark)
CVR:      AND(ISNUMBER(current),ISNUMBER(benchmark),current>benchmark)
ACOS:     AND(ISNUMBER(current),ISNUMBER(benchmark),current<benchmark)
5秒率:    AND(ISNUMBER(current),ISNUMBER(benchmark),current>benchmark)
完播率:   AND(ISNUMBER(current),ISNUMBER(benchmark),current>benchmark)
```

Use relative row references and fixed resolved columns as appropriate. Blank, text, missing, and error values must not turn green. Apply solid green `#92D050`; preserve an existing equivalent green rule when present.

## Two-row header contract

- First header row: a short `VS:` note naming the benchmark and whether smaller or larger is better.
- Second header row: `花费`, `CPC`, `点击率`, `转化率`, `ACOS`, `5秒观看率`, `完播率`.
- Use the local pale-orange header fill and centered wrapped text. Use red note text for all-channel comparisons and purple note text for video comparisons when matching the reference style.
- Format Spend and CPC as ordinary numbers matching the source; format CTR, CVR, ACOS, 5-second view rate, and completion rate as percentages matching source precision.

## Example check

If a row has current CPC `0.24` and parent-ASIN six-month all-channel CPC `0.2577`, CPC is green because `0.24 <= 0.2577`. If current CTR is `0.87%` and the parent-ASIN six-month video CTR is `1.245%`, CTR is not green. Spend has no green rule in either case.

## Verification checklist

- Confirm source and benchmark fields came from the correct top-level groups.
- Check at least one green, one non-green, and one missing/error case for every rule.
- Confirm Spend has no conditional formatting.
- Confirm the applied range ends at the last actual data row.
- Scan for `#REF!`, `#DIV/0!`, `#VALUE!`, `#NAME?`, and newly introduced `#N/A`.
- Render the complete new block and confirm headers, numbers, fills, and row alignment are visible.
