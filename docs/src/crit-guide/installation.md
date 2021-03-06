# Installation

### Install from helper script

Run the following in your terminal to download the latest version of crit:

```sh
curl -sSfL https://get.crit.sh | sh
```

By default, the latest release version is installed.  Set environment variables to install a different version, or to install to a different destination:

```sh
curl -sSfL https://get.crit.sh | VERSION=1.0.8 INSTALL_DIR=$HOME/bin sh
```

### Install From Packagecloud.io

Debian/Ubuntu:

```sh
curl -sL https://packagecloud.io/criticalstack/public/gpgkey | apt-key add -
apt-add-repository https://packagecloud.io/criticalstack/public/ubuntu
apt-get install -y criticalstack e2d
```

Fedora:

```sh
dnf config-manager --add-repo https://packagecloud.io/criticalstack/public/fedora
dnf install -y criticalstack e2d
```

### Install from GH releases

Download a binary release from [https://github.com/criticalstack/crit/releases/latest](https://github.com/criticalstack/crit/releases/latest) suitable for your system and then install, for example:

```sh
curl -sLO https://github.com/criticalstack/crit/releases/download/v1.0.1/crit_1.0.1_Linux_x86_64.tar.gz
tar xzf crit_0.2.9_Linux_x86_64.tar.gz
mv crit /usr/local/bin/
```

Please note, installing from a GH release will not automatically install the [systemd kubelet drop in](https://raw.githubusercontent.com/criticalstack/crit/master/build/package/20-crit.conf):
 
```sh
mkdir -p /etc/systemd/system/kubelet.service.d
curl -sLO https://raw.githubusercontent.com/criticalstack/crit/master/build/package/20-crit.conf
mv 20-crit.conf /etc/systemd/system/kubelet.service.d/
systemctl daemon-reload
```
