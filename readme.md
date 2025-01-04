
参数说明<br>
也可直接使用cmd带参执行原程序，例如：cfnat-windows-amd64.exe -addr="0.0.0.0:1234" -colo=HKG -delay=100 -port=80 -tls=false<br>
在国内中转机上去转发套了CDN的节点使用如下命令：cfnat-windows-amd64.exe -addr="0.0.0.0:1234" -colo=HKG -delay=100 -port=443 -tls=true<br>
  -addr string<br>
        服务端口: 本地监听的 IP 和端口 (default "0.0.0.0:1234")<br>
  -code int<br>
        HTTP/HTTPS 响应状态码 (default 200)<br>
  -colo string<br>
        数据中心: 筛选数据中心例如 HKG,SJC,LAX (多个数据中心用逗号隔开,留空则忽略匹配)<br>
  -delay int<br>
        有效延迟（毫秒）: 超过此延迟将断开连接 (default 300)<br>
  -domain string<br>
        响应状态码检查的域名地址 (default "cloudflaremirrors.com/debian")<br>
  -ipnum int<br>
        有效IP数: 提取的有效IP数量 (default 20)<br>
  -ips string<br>
        转发IP类型: 指定生成IPv4还是IPv6地址 (4或6) (default "4")<br>
  -num int<br>
        负载IP数: 目标负载 IP 数量 (default 10)<br>
  -port int<br>
        转发目标端口 (default 443)<br>
  -random<br>
        是否随机生成IP，如果为false，则从CIDR中拆分出所有IP (default true)<br>
  -tls<br>
        是否为 TLS 端口 (default true)<br>
  -task int<br>
        最大并发请求数: 并发请求最大协程数 (default 100)<br>
