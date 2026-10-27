# Home Assistant Add-ons

个人插件仓库，目前只包含 DDNS-GO。

## 安装

在 Home Assistant「设置 → 应用（或加载项）→ 应用商店 → 右上角菜单 → 仓库」添加：

```text
https://github.com/ningyuv/hassio-addons
```

刷新商店，安装并启动 DDNS-GO，点击「打开 Web UI」。也可在局域网访问 `http://Home-Assistant-IP:9876`，首次设置管理员账号，再配置 DNS 服务商和域名。

## 运行方式

- 直接使用官方 `jeessy/ddns-go:v6.17.7`，不构建、不修改镜像。
- 支持 amd64、aarch64，主机网络支持网卡地址获取及 IPv6；9876 端口需空闲。
- 设置容器环境变量 `HOME=/data`，配置保存为 `/data/.ddns_go_config.yaml`，重启、升级保留，并随插件备份保存。配置含服务商密钥，请勿提交到 GitHub。
- 默认每 300 秒检查一次，域名等业务配置在 DDNS-GO 网页完成。保留官方启动命令，不提供参考插件的 `ddnsgo_time_seconds` 选项。
- 不申请 Home Assistant 或 Supervisor API 权限。网页为 HTTP，请在可信局域网内访问。
- 从其他插件迁移时请先备份并停用旧插件；新插件不会自动导入旧配置。

## 更新

将 `ddns-go/config.yaml` 的 `version` 改为 Docker Hub 中已有的官方版本标签（包含 `v` 前缀），提交后在 Home Assistant 刷新并更新。`image` 不带标签，Supervisor 自动使用 `version`。

## 来源

- 结构参考：[dscao/hassio-addons](https://github.com/dscao/hassio-addons/tree/main/ddns-go)
- 上游项目：[jeessy2/ddns-go](https://github.com/jeessy2/ddns-go)
- 官方镜像：[jeessy/ddns-go](https://hub.docker.com/r/jeessy/ddns-go)

仅提供 Home Assistant 插件元数据，未复制上游程序及参考仓库启动脚本。
