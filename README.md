 ![Ansible Role](https://img.shields.io/ansible/role/d/9539)
 
 # ahuffman.yp

An Ansible role to configure yp.conf and ypbind NIS service.


 ## Role Variables
| Variable Name | Description | Required | Default Value | Type |
|---|---|:---:|:---:|:---:|
|yp_bind_pkg|The package name for ypbind.  You could change to a particular packagename.version if required and setup for your distribution.| no | ypbind | string |
|yp_bind_svc|The name of the ypbind service. | no | ypbind | string |
|yp_nisdomain|NIS Domain name.|yes|""|string|
|yp_nisserver|List of NIS servers for your domain.|yes|[]|list|
|yp_domain_broadcast|Whether or not to use broadcast on your local domain|no|False|boolean|
|yp_domain_slp|Query local SLP server for ypserver supporting NISDOMAIN|no|False|boolean|
|yp_server|Server hostname of your local domain.  Must be listed in /etc/hosts (see `man yp.conf`).|yes|""|string|
|yp_broadcast|If no server for the default domain is specified or none of them is reachable, try a broadcast call to find a server.|no|False|boolean|
|yp_conf_path|Path to your yp configuration file.|no|"/etc/yp.conf"|string|

## Example Playbook  
```yaml
- name: "Configure yp.conf on my servers"
  hosts: all
  roles:
    - role: "ahuffman.yp"
      yp_nisdomain: "mydomain.com"
      yp_nisserver:
        - "nis1.mydomain.com"
        - "nis2.mydomain.com"
      yp_domain_broadcast: True
      yp_domain_slp: True
      yp_broadcast: True
```

## License
[MIT](LICENSE)  

## Author
[Andrew J. Huffman](https://github.com/ahuffman)
