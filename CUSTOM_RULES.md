# 自维护 sing-box 规则

当前自维护发布仓库：git@github.com:Napoleon314/meta-rules-dat.git，分支 sing。
本地 sing 跟踪 napoleon/sing；origin 保留为 MetaCubeX 官方上游。

## 中国 IP 补充规则

2026-11-17 从 qljsyph/ruleset-icon 的固定提交 5220b40f3e43e48e2e9b2680ce4c4500142e5cd3 导入：

| 原始路径 | 当前路径 | SHA-256 |
|---|---|---|
| sing-box/geoip/China-ASN-combined-ip.json | geo/geoip/China-ASN-combined-ip.json | 0c808113d9cc893c337e56d89f3fe68372dd5aefdb46f763c750d68783e53757 |
| sing-box/geoip/China-ASN-combined-ip.srs | geo/geoip/China-ASN-combined-ip.srs | 9dd03516e02a3e147e0e08be167d5fb2cd12c210ea6affccdfbbc6caf821d046 |

来源：https://github.com/qljsyph/ruleset-icon/tree/5220b40f3e43e48e2e9b2680ce4c4500142e5cd3/sing-box/geoip

源 JSON 和已发布 SRS 成对保留，按原始字节复制，未重新编译或改变 IP 内容。
该规则对应原 wrt profile 的 geoip-cn，独立保留文件名；没有替换上游 geo/geoip/cn
或将其与上游中国 IP 集合做去重/并集，以保持现有分流规则的匹配范围。

提交并推送后，可由以下稳定地址提供给远程 rule-set：
https://raw.githubusercontent.com/Napoleon314/meta-rules-dat/sing/geo/geoip/China-ASN-combined-ip.srs

本次仅导入数据，未改变路由器主配置、部署、编译或运行验证。以后修改 JSON 时需
同步生成并发布兼容目标 sing-box 核心的 SRS；只提交 JSON 不会更新使用 binary 的客户端。

## 保留定制内容

MetaCubeX 的 master 工作流会重新生成并强推 sing 发布分支。自己的 master 若沿用
该工作流，必须先调整生成步骤以保留/重新加入本规则及来源说明，再启用自动发布；
仅修改当前 sing 分支不能防止后续生成覆盖。本文只记录此约束，本次没有修改工作流。

## 附加分流规则

`home/wrt/` 提供 PlayStation 下载域名与 Google DNS 例外两份 Source JSON。
生成 `sing` 分支时保留这些文件及[规则说明](home/wrt/README.md)。
