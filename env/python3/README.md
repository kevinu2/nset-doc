## Install compiler
`yum -y install gcc make`

## Install dependent packages
`yum -y install readline readline-devel zlib-devel libffi-devel openssl-devel bzip2-devel libuuid-devel sqlite-devel xz-devel gdbm-devel tk-devel`

## Donwload python source code
`version=3.9.4`<br />
`wget  https://www.python.org/ftp/python/${version}/Python-${version}.tar.xz`<br />
`tar Jxf Python-${version}.tar.xz`<br />
`cd Python-${version}`

## Configure, make & make install
`path=/opt/nset/py3`<br />
`./configure --prefix=${path} --enable-optimization`<br />
`make; make install`<br />

## Init bin path
`version=3.9.4`<br />
`v=${version%%.*}`<br />
`vv=${version%.*}`<br />
`path=/opt/nset/py3`<br />
`alternatives --install /usr/bin/python${v} python${v} ${path}/bin/python${v} 0`<br />
`alternatives --install /usr/bin/pip${v} pip${v} ${path}/bin/pip${v}`<br />
`alternatives --install /usr/bin/python${vv} python${vv} ${path}/bin/python${vv} 0`<br />
`alternatives --install /usr/bin/pip${vv} pip${vv} ${path}/bin/pip${vv} 0`<br />

## Change install source
`mkdir -p ~/.pip`<br />
`cat > ~/.pip/pip.conf << EOF`<br />
`[global]`<br />
`index-url = https://mirrors.aliyun.com/pypi/simple/`<br />
<br />
`[install]`<br />
`trusted-host=mirrors.aliyun.com`<br />
`EOF`<br />

## Upgrade pip
`pip3 install --upgrade pip`<br />
