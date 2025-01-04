首先声明，这款软件并非我原创开发，而是目前了解到由 股神 在 CF中转IP 频道 https://t.me/CF_NAT/38840 发布的一款实时筛选 Cloudflare 数据中心的软件。

CFNAT 是一款自动查找并优化 Cloudflare IP 转发的工具，旨在解决泛播 IP 路由不稳定的问题。如果你曾找到过速度不错的 Cloudflare IP，CFNAT 能帮助你快速筛选出最佳 IP 并实现端口转发，从而提升网络使用体验。因此，这款工具对于移动、广电网络用户来说尤为明显！有了它，绝大多数用户网络环境下用cf中转ip意义就不大了。
其中高阶用法是修改同目录下的ips-v4.txt和ips-v6.txt
用上面的colo工具找适合自己的cidr地址段。
<hr>
参数说明<br>
也可直接使用cmd带参执行原程序，例如：<code>cfnat-windows-amd64.exe -addr="0.0.0.0:1234" -colo=HKG -delay=100 -port=80 -tls=false</code><br>
在国内中转机上去转发套了CDN的节点使用如下命令：<code>cfnat-windows-amd64.exe -addr="0.0.0.0:1234" -colo=HKG -delay=100 -port=443 -tls=true</code><br>
</hr>
  <code>-addr string</code><br>
        服务端口: 本地监听的 IP 和端口 (default "0.0.0.0:1234")<br>
  <code>-code int</code><br>
        HTTP/HTTPS 响应状态码 (default 200)<br>
 <code> -colo string</code><br>
        数据中心: 筛选数据中心例如 HKG,SJC,LAX (多个数据中心用逗号隔开,留空则忽略匹配)<br>
  <code>-delay int</code><br>
        有效延迟（毫秒）: 超过此延迟将断开连接 (default 300)<br>
  <code>-domain string</code><br>
        响应状态码检查的域名地址 (default "cloudflaremirrors.com/debian")<br>
  <code>-ipnum int</code><br>
        有效IP数: 提取的有效IP数量 (default 20)<br>
  <code>-ips string</code><br>
        转发IP类型: 指定生成IPv4还是IPv6地址 (4或6) (default "4")<br>
  <code>-num int</code><br>
        负载IP数: 目标负载 IP 数量 (default 10)<br>
  <code>-port int</code><br>
        转发目标端口 (default 443)<br>
  <code>-random</code><br>
        是否随机生成IP，如果为false，则从CIDR中拆分出所有IP (default true)<br>
  <code>-tls</code><br>
        是否为 TLS 端口 (default true)<br>
  <code>-task int</code><br>
        最大并发请求数: 并发请求最大协程数 (default 100)<br>
<hr>
其中的<br>
-colo 参数提供指定数据中心的筛选  <br>
-delay 参数提供极限的链路优化，超过1000就失去了意义，该参数用于tcp目标ip连接超时判断<br>
-domain 参数用来trace指定的域名，避免某些ip只能被官方ip使用而个人免费的域名不可用<br>
 -ipnum 参数用来colo提取过程中按照延迟排序候选指定的ip数量作为待中转的ip<br>
  -tls 参数要与 -port 参数配合使用 具体cf有哪些端口是tls端口  哪些端口是非tls端口 参考 https://developers.cloudflare.com/fundamentals/reference/network-ports/
