###Creation VM by ansible in MSDC###
 
connect to the msdc ansible host  

```bash
ssh anscm-tlsmsdc01.ds.dtveng.net
```

install Python API for interacting with the vSphere Web Services SDK

```bash
easy_install -U pysphere
```
Create playbook.yml

```bash
vi createvm.yml
```

In msdc lab ansible host we have following version of python, so we need to use - validate_certs: `false`

[root@anscm-tlsmsdc01 ~]# python --version

Python 2.7.6

```bash
Validate SSL certs. Note, if running on python without SSLContext support (typically, python < 2.7.9) 
you will have to set this to no as pysphere does not support validating certificates on older python. 
Prior to 2.1, this module would always validate on python >= 2.7.9 and never validate on python <= 2.7.8.
```

Lets create some VMs with ansible

```bash
ansible-playbook createvm.yml -i localhost
```

Links:
* http://docs.ansible.com/ansible/latest/vsphere_guest_module.html
* https://pypi.python.org/pypi/pysphere