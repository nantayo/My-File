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
# dns
dip(1.0.0.1,8.8.4.4) -> hk

# passthrough
mac("34:5F:45:5C:5A:4F") -> must_direct
pname(NetworkManager,systemd-resolved,dnsmasq,mosdns,zerotier) -> must_direct

# direct
dip(geoip:private) -> direct
domain(geosite:private) -> direct
!dport(80,443,853) -> direct

# proxy
domain(geosite:pixiv) -> jp
domain(geosite:bing,geosite:gfw) -> hk

# fallback
fallback: direct
```