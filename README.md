# DNS – Currently the Linux based servers do not register with DNS and need to be manually registered. This is to be automated

Added to sssd.conf, as the standard way to configure this.

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/windows_integration_guide/sssd-dyndns

# Hosts File – The local host name of the system is not entered into the hosts file, which often breaks applications deployed post build such as EAP

Done via ansible

# AD Domain Join function – Move Computer account in AD from Computers OU to Servers/Linux OU.

Added to realmd.conf as the standard way to configure this.

However, if you wish to continue using the command line for this, amend your existing ansible role to state:

```
realm join --computer-ou="ou=Servers,ou=Linux,dc=domain,dc=com" --user={{ ad_domain_username }} {{ ad_domain_dname }}
```

https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/windows_integration_guide/realmd-conf

# Install both NFS and SMB client tools for access to these resources.

Done, includes nfs mount and samba configs
