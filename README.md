•DNS – Currently the Linux based servers do not register with DNS and need to be manually registered. This is to be automated

Added to realm.conf, please also see:
https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/windows_integration_guide/sssd-dyndns

•Hosts File – The local host name of the system is not entered into the hosts file,
which often breaks applications deployed post build such as EAP

Done via ansible

•AD Domain Join function – Move Computer account in AD from Computers OU to Servers/Linux OU.

Expand existing realm join to include (see below), although a better way would
to use the realm.conf provided (replace content with your own requirements/environment)

```
realm join --computer-ou="ou=Servers,ou=Linux,dc=domain,dc=com" --user={{ ad_domain_username }} {{ ad_domain_dname }}
```

•Install both NFS and SMB client tools for access to these resources.

Done, includes nfs mount and samba configs
