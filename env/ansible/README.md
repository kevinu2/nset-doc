## Install python3 env
<https://github.com/kevinu2/nset-doc/tree/master/env/python3>

## Install ansible
`path=/opt/nset/py3`<br />
`pip3 install ansible`<br />
`alternatives --install /usr/bin/ansible-playbook ansible-playbook ${path}/bin/ansible-playbook 0`<br />
`alternatives --install /usr/bin/ansible ansible ${path}/bin/ansible 0`

## Install module for K8S
`pip3 install openshift`

## Install module for ETCD
`pip3 install etcd3`

## Install pssh
`git clone https://github.com/lilydjwg/pssh.git`<br />
`cd pssh`<br />
`python3 setup.py install`

## Change default python env
`path=/opt/nset/py3`<br />
`site_pkgs=${path}/lib/python3.9/site-packages`<br />
`find ${site_pkgs} -name "*.py" -exec sed -i 's#/usr/bin/python#${path}/bin/python3#g' {} \;`
