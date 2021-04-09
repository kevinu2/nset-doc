## Install compiler
`yum -y install gcc make`

## Install dependent packagesCancel changes
`yum -y install readline readline-devel zlib-devel libffi-devel openssl-devel`

## Donwload python source code
py_version=3.9.4
`wget https://www.python.org/ftp/python/${py_version}/Python-${py_version}.tgz`<br />
`tar zxf Python-${py_version}.tgz`<br />
`cd Python-${py_version}`

## Configure, make & make install
`./configure --prefix=/opt/nset/py3 --enable-optimizations --with-ssl`<br />
`make; make install`<br />

## Init bin path
`alternatives --install /usr/bin/python3 python3 /opt/nset/py3/bin/python3 0`<br />
`alternatives --install /usr/bin/pip3 pip3 /opt/nset/py3/bin/pip3 0`<br />

## Upgrade pip
`pip3 install --upgrade pip`
