## Install compiler
Debian/Ubuntu
```
apt-get -y install gcc make
```
CentOS
```
yum -y install gcc make
```

## Install dependent packages
Debian/Ubuntu
```
apt-get -y install libreadline-dev zlib1g-dev libffi-dev libssl-dev uuid-dev libgdbm-dev tk-dev libsqlite3-dev libbz2-dev liblzma-dev
```
CentOS
```
yum -y install readline readline-devel zlib-devel libffi-devel openssl-devel bzip2-devel libuuid-devel sqlite-devel xz-devel gdbm-devel tk-devel
```
## Donwload python source code
```
version=3.9.7
wget -c https://www.python.org/ftp/python/${version}/Python-${version}.tar.xz
tar Jxf Python-${version}.tar.xz
cd Python-${version}
```

## Configure, make & make install
```
path=/opt/python3
./configure --prefix=${path}
make; make install
```

## Init bin path
```
version=3.9.7
v=${version%%.*}
vv=${version%.*}
path=/opt/python3
```
CentOS
```
alternatives --install /usr/local/bin/python${v} python${v} ${path}/bin/python${v} 0
alternatives --install /usr/local/bin/pip${v} pip${v} ${path}/bin/pip${v} 0
alternatives --install /usr/local/bin/python${vv} python${vv} ${path}/bin/python${vv} 0
alternatives --install /usr/local/bin/pip${vv} pip${vv} ${path}/bin/pip${vv} 0
```
Debian/Ubuntu
```
update-alternatives --install /usr/local/bin/python${v} python${v} ${path}/bin/python${v} 0
update-alternatives --install /usr/local/bin/pip${v} pip${v} ${path}/bin/pip${v} 0
update-alternatives --install /usr/local/bin/python${vv} python${vv} ${path}/bin/python${vv} 0
update-alternatives --install /usr/local/bin/pip${vv} pip${vv} ${path}/bin/pip${vv} 0
```

## Change install source
```
mkdir -p ~/.pip
cat > ~/.pip/pip.conf << EOF
[global]
index-url = https://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host=mirrors.aliyun.com
EOF
```

## Upgrade pip
```
pip3 install --upgrade pip
```

## Quick fix
Ubuntu
```
ln -s /usr/share/pyshared/lsb_release.py /opt/python3/lib/python3.9/site-packages/
sed -i 's@/usr/bin/python.*@/opt/python3/bin/python3@g' /usr/bin/lsb_release
```
