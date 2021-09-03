# x-ui
Support multi-protocol and multi-user xray panel

# Features
- System status monitoring
- Support multi-user and multi-protocol, web page visualization operation
- Supported protocols: vmess, vless, trojan, shadowsocks, dokodemo-door, socks, http
- Support to configure more transmission configurations
- Traffic statistics, limit traffic, limit expiration time
- Customizable xray configuration template
- Support https access panel (bring your own domain name + ssl certificate)
- More advanced configuration items, see the panel for details

# Installation & Upgrade
```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

## Manual installation & upgrade
1. First download the latest compressed package from https://github.com/vaxilu/x-ui/releases, generally choose the `amd64` architecture
2. Then upload the compressed package to the `/root/` directory of the server, and use the `root` user to log in to the server

> If your server cpu architecture is not `amd64`, replace `amd64` in the command with another architecture

```
cd /root/
rm x-ui/ /usr/local/x-ui/ /usr/bin/x-ui -rf
tar zxvf x-ui-linux-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-linux-* x-ui/x-ui.sh
cp x-ui/x-ui.sh /usr/bin/x-ui
cp -f x-ui/x-ui.service /etc/systemd/system/
mv x-ui/ /usr/local/
systemctl daemon-reload
systemctl enable x-ui
systemctl restart x-ui
```

## Suggestion System
-CentOS 7+
-Ubuntu 16+
-Debian 8+

# common problem

## Migrate from v2-ui
First install the latest version of x-ui on the server where v2-ui is installed, and then use the following command to migrate, which will migrate the `all inbound account data` of the machine's v2-ui to x-ui, `panel settings and username and password Will not migrate`
> After the migration is successful, please `close v2-ui` and `restart x-ui`, otherwise the inbound of v2-ui and the inbound of x-ui will cause a `port conflict`
```
x-ui v2-ui
```

