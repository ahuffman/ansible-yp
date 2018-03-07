 # ahuffman.yp

An Ansible role to configure yp.conf and ypbind NIS service.


 ## Role Variables

### Defaults
`ypbindpkg`: 'ypbind'  
The packagename for ypbind.  You could change to a particular packagename.version if required and setup for your distribution.

`ypbindsvc`: 'ypbind'  
The service name for EL systems.  You could change the name to fit your distribution.

`yp_nisdomain`: ''  
NIS Domain name.

`yp_nisserver`: []  
List of NIS servers for your domain.

`yp_domain_broadcast`: 'false'  
Use broadcast on your local domain

`yp_domain_slp`: 'false'  
Query local SLP server for ypserver supporting NISDOMAIN

`yp_server`: ''  
Server hostname of your local domain.  Must be listed in /etc/hosts (man yp.conf)

`yp_broadcast`: 'false'  
If no server for the default domain is specified or none of them is rechable, try a broadcast call to find a server.  

`yp_conf_path`: '/etc/yp.conf'  
Path to your yp configuration file.  

 ## Example Playbook  

    - hosts: all
      vars:
        yp_nisdomain: mydomain.com
        yp_nisserver:
          - nis1.mydomain.com
          - nis2.mydomain.com
        yp_domain_broadcast: true
        yp_domain_slp: true
        yp_broadcast: true
      roles:
         - ahuffman.yp


 ## License  
[MIT](LICENSE)  

 ## Author Information  
[Andrew J. Huffman](https://github.com/ahuffman)
