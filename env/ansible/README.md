## Install python3 env
<https://github.com/kevinu2/nset-doc/tree/master/env/python3>

## Install ansible
```
path=/opt/python3
pip3 install ansible
```
CentOS
```
alternatives --install /usr/local/bin/ansible-playbook ansible-playbook ${path}/bin/ansible-playbook 0
alternatives --install /usr/local/bin/ansible ansible ${path}/bin/ansible 0
```
Debian/Ubuntu
```
update-alternatives --install /usr/local/bin/ansible-playbook ansible-playbook ${path}/bin/ansible-playbook 0
update-alternatives --install /usr/local/bin/ansible ansible ${path}/bin/ansible 0
```

## Install module for K8S
```
pip3 install openshift
```

## Install module for ETCD
```
pip3 install etcd3
```

## Install pssh
```
git clone https://github.com/lilydjwg/pssh.git
cd pssh
python3 setup.py install
```

## Change default python env
```
for py in `find /opt/python3/lib/python3.9/site-packages -type f -name "*.py*"`; do
  if [ `grep '/usr/bin/python' $py -c` -gt 0 ]; then
    echo $py
    sed -i 's@/usr/bin/python@/opt/python3/bin/python3@g' $py
  fi
done
```
