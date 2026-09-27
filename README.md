# ZodAccess API 域名规则

`rules/custom-api.json` 和 `rules/custom-api.srs` 只包含 `dragon3api.com` 与 `yujianwudi.top`，便于单独使用。

`geo/geosite/geolocation-!cn.json` 和对应的 `.srs` 保留了 [MetaCubeX geolocation-!cn](https://github.com/MetaCubeX/meta-rules-dat/tree/sing/geo/geosite) 的原有规则，并额外加入这两个域名后缀。基础数据取自 `sing` 分支提交 `6fea7d2d9bc4c7f85d2b8ff46d3f3250d09c0d12`；原有 26,306 条后缀全部保留，合并后为 26,308 条。派生数据和源文件按上游 GPL-3.0 许可证提供，详见 `LICENSE`。

## ZodAccess 6.0.16 中的用法

将现有 `geolocation-!cn.srs` 那一项的 URL **替换**为：

```text
https://raw.githubusercontent.com/feNgL2025/custom-api-rules/main/geo/geosite/geolocation-!cn.srs
```

保持该项原有的“反转规则”状态。不要把它作为一条新 URL 追加。当前 ZodAccess 配置会引用 `geosite-geolocation-!cn` 标签，将它匹配的域名交给代理，并跳过后面的 `resolve` 步骤；额外添加的 `custom-api` 标签目前没有对应的路由规则。

这份合并规则集是 2026-09-27 的上游快照。上游名单更新时，需要重新合并并编译。编译命令：

```text
sing-box rule-set compile --output geo/geosite/geolocation-!cn.srs geo/geosite/geolocation-!cn.json
```
