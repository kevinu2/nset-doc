## Install 'ansible env'
<https://github.com/kevinu2/nset-doc/tree/master/env/ansible>

## Download 'nset-modules-ansible'
`cd /opt`<br />
`git clone https://github.com/kevinu2/nset-ansible.git`<br />
`cd nset-modules-ansible`

## Use ['nset-cli'](https://github.com/kevinu2/nset-cli)

#### Opt 1. Setup hosts in ['inventory.ini'](https://github.com/kevinu2/nset-ansible/blob/master/inventory.ini.example)
`cp inventory.ini.example inventory.ini`
`vim inventory.ini`
```
[ntp_local]
s1.nset

[ntp_cluster]
s1.nset
```
__ntp__ is the module name, [Get more module name](https://github.com/kevinu2/nset-ansible/blob/master/README.md)<br />
__[ntp_local]__ is defined the hosts witch to be connected and installed modules<br />
__[ntp_cluster]__ is defined the hosts variables for templates

#### Opt 2. Setup RPM, Docker Image, Tarball in ['version.yaml'](https://github.com/kevinu2/nset-ansible/blob/master/version.yaml)
`vim version.yaml`
```
##########################
# ntp
##########################
ntp:
  rpms:
    - name: ntp
      file: ntp-4.2.6p5-29.el7.centos.x86_64.rpm
      url:  http://mirrors.aliyun.com/centos/7.9.2009/os/x86_64/Packages//ntp-4.2.6p5-29.el7.centos.x86_64.rpm
    - name: ntpdate
      file: ntpdate-4.2.6p5-29.el7.centos.x86_64.rpm
      url: http://mirrors.aliyun.com/centos/7.9.2009/os/x86_64/Packages//ntpdate-4.2.6p5-29.el7.centos.x86_64.rpm
    - name: autogen-libopts
      file: autogen-libopts-5.18-5.el7.x86_64.rpm
      url: http://mirrors.aliyun.com/centos/7.9.2009/os/x86_64/Packages//autogen-libopts-5.18-5.el7.x86_64.rpm
```

#### Opt 3. Setup the customize variables in ['config_local.yaml'](https://github.com/kevinu2/nset-ansible/blob/master/config_local.yaml)
`vim config_local.yaml`
```
####################
# Environment
####################

deploy_data_path: "/home/data"
ceph_devices:
  - /dev/sdb 
elasticsearch_admin_user: 'es'
elasticsearch_admin_password: 'yourpassword'
```

## Start the progress with ['nset-cli'](https://github.com/kevinu2/nset-cli)
#### Install single module
`./nset-cli install -m ntp`
#### Install multiple modules one by one
`./nset-cli install -m ntp,dnsmasq`
