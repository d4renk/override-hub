# override-hub 项目说明

自用的 mihomo 覆写配置、Shadowrocket 配置与 Sub-Store 组合订阅模板。

---

## 声明与兼容性

- 托管与覆写配置已在 **Sub-Store** 中测试通过。
- **mihomo-party / sparkle** 等客户端请自行测试，本项目在此类客户端上的兼容性不做保证，请谨慎使用。

---

## 可用文件列表

### 1. mihomo (Clash Meta) 配置文件
提供远程解析与本地分流两个版本，请按自己的 DNS 使用方式选择。

- **远程 DNS 覆写配置**：[selfuse_test_remote.yaml](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/selfuse_test_remote.yaml)
- **远程 DNS 覆写配置（IPv4 代理解析版）**：[selfuse_test_remote_ipv4_resolve.yaml](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/selfuse_test_remote_ipv4_resolve.yaml)
  - 适合直连网络只能使用运营商 DNS、且普通 DIRECT 不可用的环境：启动和代理节点解析使用系统 DNS，业务 DoH 通过 `节点选择` 代理组访问，`全球直连` 默认优先使用代理出口。
- **本地 DNS 分流配置**：[selfuse_test_local.yaml](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/selfuse_test_local.yaml)

### 2. Shadowrocket 配置文件
- **Shadowrocket 配置文件**：[Shadowrocket.conf](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/Shadowrocket.conf)
  - 分组和分流规则与 mihomo 覆写配置基本保持一致。

### 3. Sub-Store 组合订阅模板
- **通用组合订阅模板**：[sub-store组合订阅模板.json](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/sub-store%E7%BB%84%E5%90%88%E8%AE%A2%E9%98%85%E6%A8%A1%E6%9D%BF.json)
  - 功能包括：节点重命名、节点排序、过滤风险节点、替换国旗/旗帜、IPv6 入口解析（可选）、多机场流量信息整合、以及家宽/落地节点自动设置代理链（可选）。
- **IPv4 解析版组合订阅模板（新增）**：[sub-store组合订阅模板-ipv4解析.json](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/sub-store%E7%BB%84%E5%90%88%E8%AE%A2%E9%98%85%E6%A8%A1%E6%9D%BF-ipv4%E8%A7%A3%E6%9E%90.json)
  - **功能说明**：基于通用组合订阅模板扩展。该模板会额外检测订阅名、订阅显示名或节点名；命中“自建”或“直连”关键字时，会把对应的代理服务器域名解析为 IPv4 地址后下发。
  - **特性与限制**：
    - 仅解析并下发 IPv4 地址。
    - 若域名解析失败，将保留原始域名，不影响连接。
    - 该修改为独立文件，原有的通用组合订阅模板不受任何影响。

### 4. Sub-Store 托管配置模板
- **mihomo 托管配置**：[mihomo配置.json](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/mihomo%E9%85%8D%E7%BD%AE.json)
- **singbox 托管配置**：[singbox配置.json](https://raw.githubusercontent.com/d4renk/override-hub/refs/heads/main/singbox%E9%85%8D%E7%BD%AE.json)

---

## 使用指南

### 1. Sub-Store 组合订阅模板导入
1. 打开 Sub-Store 订阅管理页面，点击左上角加号。
2. 选择导入本地配置，填入对应的模板 raw 链接。
3. 选择需要整合的机场订阅并保存。
4. 推荐配合查看[图文版教程](https://linux.do/t/topic/660141/86)。

### 2. Sub-Store 托管配置导入
1. 打开 Sub-Store 文件管理页面，点击左上角加号。
2. 选择导入本地配置，填入对应的托管配置 raw 链接（mihomo配置 或 singbox配置）。

---

## 致谢

本项目的实现离不开以下优秀开源项目与社区的技术分享与支持，在此表示诚挚的谢意（排名不分先后）：

- [mihomo-party-org/override-hub](https://github.com/mihomo-party-org/override-hub)
- [Keywos/Rule](https://github.com/Keywos/Rule)
- [cmliu/ACL4SSR](https://github.com/cmliu/ACL4SSR)
- [teishahbc/bgp-cn-ip](https://github.com/teishahbc/bgp-cn-ip)
- [SukkaW/Surge](https://github.com/SukkaW/Surge)
- [DustinWin/ruleset_geodata](https://github.com/DustinWin/ruleset_geodata)
- [Repcz/Tool](https://github.com/Repcz/Tool)
- linux.do 社区分享：[帖子 496229](https://linux.do/t/topic/496229)
- 折腾啥 Telegram 频道：[zhetengsha/2197](https://t.me/zhetengsha/2197)
