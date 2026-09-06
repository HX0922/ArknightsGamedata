# legacy/ 存量增补区

本目录存放 ArknightsGameResource 的**历史遗留存量** (旧社区仓库中有、当前版本
客户端/CDN 中已不存在的资源), 与 `gamedata/` 实时管线输出隔离共存。

## 用途

- 完整覆盖历史数据: `gamedata/` (当前) + `gamedata_legacy/` (历史) = 全版本内容
- 下游查询 (ark_story 等) 如需完整视图, 以 manifest.json 为索引做虚拟合并
  (物理文件保持隔离, 不互相污染)

## 文件

| 文件 | 说明 |
|---|---|
| `gamedata_legacy/` | 镜像旧树结构的历史资源 (1,298 文件, 158.6 MB) |
| `manifest.json` (在 ../reports/legacy-supplement-2026-08-04/) | 全量清单: 逐文件 md5/事件前缀/理由/去重标注 |
| `SOURCE.md` | 来源声明 (社区仓库 26-07-20 快照, 一次性导入, 非游戏直提) |
| `diff_report.md` (同上 reports 目录) | 三层差集全量报告 (文件级/条目级/内容级) |

## 与 gamedata/ 的关系

- `gamedata/` = 26-07-30 自建管线实时输出 (9,871 文件), 随版本更新
- `gamedata_legacy/` = 26-07-20 社区快照中独有的历史资源, 永不再更新
- 两者无重叠 (内容级验证确认): legacy 中每个文件的内容在新树中均不存在

## 查询示例

```python
# 完整视图 = gamedata + legacy (manifest 驱动)
import json
m = json.load(open("reports/legacy-supplement-2026-08-04/manifest.json"))
for f in m["files"]:
    if f["classification"] == "L":
        # 物理路径: legacy/gamedata_legacy/<rel_path>
        pass
```
