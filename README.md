<div align="center">
<img src="docs/Logo.png" width=200px>

<h1>TPClash</h1>

TPClash(Transparent proxy tool for Clash)，是一个用于 Clash 的透明代理辅助工具, 由于众所周知的原因~~手笨~~而创建的.

</div>

## 一、TPClash 是什么

TPClash 可以自动安装 ~~Clash Premium~~（已抛弃）/~~Meta~~(改名为 Mihomo), 并自动配置基于 Tun 的透明代理.

**TPClash 的透明代理规则、日志配置、Dashboard(UI) 配置等全部从标准的 Clash 配置文件内读取, 并完成自适应; TPClash 暂时不会创建自己的自定义
配置文件(减轻使用负担).**

## 二、使用教程

为了使README更加整洁干练，以突出重要内容，分成了两部分。

若您需要使用教程，请[点击这里](GUIDE.md)跳转到使用教程

（不使用GitHub Wiki的原因是因为不方便备份）

## 三、TPClash 做了什么

**TPClash 在启动后会进行如下动作:**

- 1、创建 `/data/clash` 目录(可自行指定成其他目录), 并将其作为 Clash 的 `Home Dir`
- 2、将 Clash 二进制文件、Dashboard(官方+yacd)、必要的 ruleset、Country.mmdb 释放到 `/data/clash` 目录
- 3、从本地或远程读取配置, 进行模版解析后复制到 `/data/clash/xclash.yaml`
- 4、启动官方的 Clash, 并设置必要参数, 比如 `-ext-ui`、`-d` 等
- 5、选择性进行网络配置, 例如为 Docker 用户自动设置 nftables
- 6、在后台持续监视本地或远程配置文件变动, 然后自动重载

## 四、如何编译 TPClash

由于 TPClash 是一个集成工具, 所以在编译前请安装好以下工具链:

- git
- curl
- jq
- tar
- gzip
- nodejs(用于编译 Dashboard)
- pnpm(Dashboard 编译所需依赖工具, 可通过 `npm i -g xxx` 安装)
- golang 1.21+
- [go-task](https://github.com/go-task/task)(类似 Makefile 的替代工具)

TPClash 项目内的 `Taskfile.yaml` 内已经写好了自动编译脚本, 只需要执行 `task` 命令即可:

```sh
git clone https://github.com/QingNetwork/tpclash.git
cd tpclash
task # go-task 安装成功后会包含此命令
```

**其他高级编译(例如单独编译特定平台)请执行 `task --list` 查看.**

## 五、其他说明

TPClash 默认释放的文件包含了 [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) 相关文件, 可在规则中直接使用;

**TPClash 同时也释放了 [Hackl0us/GeoIP2-CN](https://github.com/Hackl0us/GeoIP2-CN) 项目的 Country.mmdb 文件, 该 GeoIP 数据库
仅包含中国大陆地区 IP, 所以如果使用 `GEOIP,US,PROXY` 等其他国家规则会失败.**

## 六、复活版TPClash频道&讨论群

Telegram 频道: [https://t.me/tpclash](https://t.me/tpclash)

Telegram 交流群：https://t.me/+IXKJy7_SiM5mN2Q1

## Stargazers over time
[![Stargazers over time](https://starchart.cc/QingNetwork/tpclash.svg?variant=adaptive)](https://starchart.cc/QingNetwork/tpclash)
