# Xray-install

Bash脚本，用于在支持systemd的操作系统（如CentOS / Debian / OpenSUSE）中安装Xray。

[文件系统层次结构标准 （FHS）](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

```
installed: /etc/systemd/system/xray.service
installed: /etc/systemd/system/xray@.service

installed: /usr/local/bin/xray
installed: /usr/local/etc/xray/*.json

installed: /usr/local/share/xray/geoip.dat
installed: /usr/local/share/xray/geosite.dat

installed: /var/log/xray/access.log
installed: /var/log/xray/error.log
```

注意：默认情况下，Xray 不会登录。配置以指定日志文件。/var/log/xray/*.log"log"

## 基本用法

**使用`User=nobody`安装和升级Xray核心和地理数据，但不会覆盖现有服务文件中的用户**

```
bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ install
```

**仅更新地理.dat和地理站点.dat**

```
bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ install-geodata
```

**删除 Xray，但 json 和日志除外**

```
# bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ remove
```

## 进阶

**安装并将 Xray 内核升级到预发布版本**

```
bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ install --version 1.5.8
```

**使用`User=root`安装和升级 Xray 核心和地理数据，这将覆盖现有服务文件中的用户**

```
# bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ install -u root
```

**安装和升级Xray核心，无需地理数据**

```
bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ install --without-geodata
```

**删除 Xray，包括 json 和日志**

```
bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ remove --purge
```

## 更多用法

```
bash -c "$(curl -L https://ghproxy.com/https://github.com/scdlyh/install-release//main/Xray-install-release.sh)" @ help
```
