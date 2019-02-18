# wanem: A wan emulator for virtual and physical appliances

wanem is a clean web interface which remotely configure traffic control (tc)

## features: 
* automated interfaces discovery
* display the bridge interface associated to native interfaces
* limit bandwidth per interface
* adjust delay, loss and jitter per interface

## Installation

### Installing on Debian

```
apt-get update
apt-get install ruby bridge-utils lldp ruby-dev
gem install sinatra
gem install thin
git clone https://github.com/PJO2/wanem
cd wanem
ruby ./http_main.rb
```


### Installing on Cumulus Linux
ruby-dev is not a package, should be installed manually

```
wget http://security.debian.org/debian-security/pool/updates/main/r/ruby2.1/ruby2.1-dev_2.1.5-2+deb8u6_amd64.deb
wget http://ftp.us.debian.org/debian/pool/main/g/gmp/libgmp-dev_6.0.0+dfsg-6_amd64.deb
wget http://ftp.us.debian.org/debian/pool/main/g/gmp/libgmpxx4ldbl_6.0.0+dfsg-6_amd64.deb

dpkg -i libgmpxx4ldbl_6.0.0+dfsg-6_amd64.deb
dpkg -i libgmp-dev_6.0.0+dfsg-6_amd64.deb
dpkg -i ruby2.1-dev_2.1.5-2+deb8u6_amd64.deb

gem install sinatra:1.4.8
gem install thin
git clone https://github.com/PJO2/wanem
cd wanem
ruby ./http_main.rb
```


### Installing on CentOs

```
yum install epel-release
yum update

yum group info "Development Tools"
yum install bridge-utils lldpd ruby ruby-dev
gem install sinatra:1.4.8
gem install thin

service NetworkManager stop
systemctl disable NetworkManager.service

git clone https://github.com/PJO2/wanem
cd wanem
ruby ./http_main.rb
```

## making wanem start on boot

```
crontab -e
add a line : 
@reboot (export PATH='/bin:/sbin:/usr/bin:/usr/sbin' && cd home/ark/wanem && ruby http_main.rb &> /dev/null &)
```
