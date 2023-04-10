# Sakari 的 Linux 网络配置仓库

[使用dae和clash实现的全局代理方案](https://sakari.top/2023/dae-clash/)

## 使用项目

- [dae](https://github.com/daeuniverse/dae)：高性能全局透明代理
- [Clash.Meta](https://github.com/MetaCubeX/Clash.Meta/tree/Meta)：作为 dae 的上游提供代理
- [caddy](https://github.com/caddyserver/caddy)：可选，为某些受到 SNI 阻断的服务提供直连

## 安装

- [dae](https://github.com/daeuniverse/dae/blob/main/docs/getting-started/README_zh.md)，注意 dae 对内核版本有要求

- 一个正常工作的代理客户端，`clash`、`clash-meta`、`clash for windows`、`v2ray` 等均可

## 配置

### clash

本节可跳过，可使用现有的正常工作的配置文件，仅需要保证 clash 的端口和 dae node 中配置的一致。与 dae 共同使用时请保证代理的各种全局代理方案（tun、iptables 等）均已关闭

#### 转换订阅

自行搭建 [proxy-provider-converter](https://github.com/qier222/proxy-provider-converter)，或使用 [proxy-converter.sakari.top](https://proxy-converter.sakari.top/)，将 clash 订阅转换成 `Proxy Provider` 支持的格式

#### 修改配置

编辑 [clash/config.yaml](clash/config.yaml)，将转换后的链接填入 `url` 中

下载 [Yacd-meta](https://github.com/yaling888/yacd/archive/gh-pages.zip)，解压至配置文件中 `external-ui` 所在目录

根据需要修改分流规则

### dae

修改 [dae/config.dae](dae/config.dae)，将 `wan_interface` 的值修改为自己的网卡，可以使用 `ip a` 查看

### caddy

无直连需求可跳过，参考 [在Linux上使用Caddy反代Steam社区](https://sakari.top/2022/steam-caddy/)