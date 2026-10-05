# Jellyfin
podman run -d --name=Jellyfin --restart=no --net=host -e TZ=Asia/Shanghai -v /opt/Config/Jellyfin/config:/config -v /opt/Config/Jellyfin/cache:/cache -v /opt/Share/当季番剧:/media/当季番剧 -v /media/Share/电影:/media/电影 -v /media/Share/往季番剧:/media/往季番剧 --device=/dev/dri:/dev/dri --label io.containers.autoupdate=registry docker.io/nyanmisaka/jellyfin:latest
***
# Mumble
podman run -d --name=Mumble --restart=no --net=host -e TZ=Asia/Shanghai -v /opt/Config/mumble:/data localhost/mumble-server:1.5.915
***
# PeerBanHelper
podman run -d --name=PeerBanHelper --restart=no --net=host -e TZ=Asia/Shanghai -v /opt/Config/PBH:/app/data/ --label io.containers.autoupdate=registry docker.io/ghostchu/peerbanhelper:latest
***
# qBittorrent
podman run -d --name=qBittorrent --restart=no --net=host -e TZ=Asia/Shanghai -v /opt/Config:/config -v /opt/Share:/download --label io.containers.autoupdate=registry docker.io/superng6/qbittorrentee:latest
***
# RSSHub
podman run -d --name=RSSHub --restart=no --net=host --env-file=/opt/Config/rsshub.env --label io.containers.autoupdate=registry docker.io/diygod/rsshub:latest
> 附注：哔哩哔哩Cookie通过[网页](https://api.vc.bilibili.com/dynamic_svr/v1/dynamic_svr/dynamic_new?uid=0&type=8)获取。