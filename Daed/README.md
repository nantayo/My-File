# DNS
```
upstream {
  mosdns: 'udp://127.0.0.1:5335'
}

routing {
  request {
    fallback: mosdns
  }
}
```
***
# 路由
```
# passthrough
domain(nantayo.v6.rocks,v51124-6.qpon) -> must_direct
mac('34:5F:45:5C:5A:4F', '54:48:E6:40:4E:BE', 'A8:16:9D:89:15:EA') -> must_direct
pname(mosdns) -> must_rules
pname(NetworkManager,systemd-resolved,dnsmasq,zeotier) -> must_direct

# direct
dip(116.116.116.116,221.5.88.88,geoip:private) -> direct
!dport(80,443,853) -> direct
domain(geosite:private) -> direct
dscp(0x4) -> direct
sport(8920,11454,64738) -> direct

# proxy
dip(1.0.0.1,8.8.4.4) -> hk
domain(geosite:pixiv) -> jp
domain(geosite:bing,geosite:gfw) -> hk

# fallback
fallback: direct
```