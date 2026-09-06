# legacy/ 来源声明 (SOURCE)

本目录是 ArknightsGameResource 项目的**历史遗留存量增补区**。

## 来源

- 仓库: Kengxxiao/ArknightsGameData (社区仓库, 跨版本累积)
- git 快照: `fa63359c02e08e0bf9c24d0b14dd14fb719a1e5c`
- 数据版本: `26-07-20-09-52-12_5d4a43` (2026-07-20 23:34 [CN UPDATE])
- 增补日期: 2026-08-04

## 性质

- 本目录内容**来源于社区仓库快照, 非游戏客户端直提**。
- 是一次性存量导入: 这些文件在当前版本 (26-07-30) 客户端/CDN 中不存在
  (懒加载 + 历史资源下架), 且**永不再随管线更新**。
- 后续版本以 `gamedata/` 实时管线输出为准; 本目录不构成对上游的持续依赖。

## 内容构成 (1,298 文件, 158.6 MB)

| 类别 | 数量 | 说明 |
|---|---|---|
| levels | 970 | 历史活动关卡 (act2multi/act1vautochess/act1sandbox... 60+ 活动) |
| story | 160 | 沙盒AVG/活动info/guide/training 文本 |
| [uc]lua | 170 | 旧活动 UI 脚本 (returnning/returnv2/actflip...) —— **源码文本** (来自社区仓库的 AES 解密产物; 与 gamedata/ 里的当前版明文 lua 为不同版本) |
| building | 1 | room_obstacle_data.json (新客户端已移除, 2026-08-04 人工复核确认归 L) |
| excel | 1 | vc/vc_config.json (2026-08-04 人工复核确认归 L) |

## lua 格式说明 (2026-08-05)

- `gamedata/[uc]lua/` = 当前版本 (26-08-03 客户端) 的 lua, **已解密为可读源码文本** (step1 管线 2026-08-05 修复: lua 是 AES-128-CBC 加密的源码文本, 非字节码; key=UITpAi82pHAWwnzq, has_rsa, iv=xor)
- `gamedata_legacy/[uc]lua/` = 历史版本 (26-07-20 社区快照) 的 lua 源码文本
- 两者均为明文源码, 版本不同; 社区仓库 (Kengxxiao/yuanyan3060) 的 lua 与自建解密产物同源 (语义一致 337/341)

(manifest 计数 1,302 = 1,298 + 4 个去重跳过文件; 去重组: act1vautochess 01-06~05-06 同字节)

## 校验

- 逐文件 md5 与 manifest.json 一致 (manifest 中 md5 为旧树源文件 md5)
- 复制时已校验, 2026-08-04 复核通过

## 约束

- 本目录**不参与**管线增量同步; 任何管线脚本不得合并写入或覆盖本目录。
- 删除/修改需人工确认。
