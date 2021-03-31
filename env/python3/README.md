## Install compiler
`yum -y install gcc make`

## Install dependent packages
`yum -y install readline readline-devel zlib-devel libffi-devel openssl-devel`

## Donwload python source code
`wget https://www.python.org/ftp/python/3.7.7/Python-3.7.7.tgz`<br />
`tar zxf Python-3.7.7.tgz`<br />
`cd Python-3.7.7`

## Configure, make & make install
`./configure --prefix=/opt/nset/py3 --enable-optimizations --with-ssl`<br />
`make; make install`<br />

## Init bin path
`alternatives --install /usr/bin/python3 python3 /opt/nset/py3/bin/python3 0`<br />
`alternatives --install /usr/bin/pip3 pip3 /opt/nset/py3/bin/pip3 0`<br />

## Upgrade pip
`pip3 install --upgrade pip`
