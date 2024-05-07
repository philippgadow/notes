## Configuration of AFS client for access to cern.ch and RZG cluster of Max-Planck Computing
_(Tested on Ubuntu 16.04)_

**Install packages:**

* openafs-client
* openafs-modules-dkms
* openafs-krb5
* krb5-user
* krb5-config

by entering the command
> $ sudo apt-get install openafs-client openafs-modules-dkms krib5-user krb5-config


#### Configure AFS client and Kerberos:

1. use "cern.ch" as default AFS cell:
  
>$ sudo echo "cern.ch" > /etc/openafs/ThisCell

2. setup kerberos5 authentication:
  add following lines to file '/etc/krb5.conf':
settings for CERN.CH realm are taken from file
_lxplus.cern.ch:/etc/krb5.conf_

==========================================>

>[libdefaults]
>  default_realm = CERN.CH
>  ticket_lifetime = 25h
>  renew_lifetime = 120h
>  forwardable = true
>  proxiable = true
>  allow_weak_crypto = true

Next two lines MAY be needed - depending on Kerberos implementation,
do not uncomment unless you see preauthentication errors on your client. 

>default_tkt_enctypes = arcfour-hmac-md5 aes256-cts aes128-cts des3-cbc-sha1 des-cbc-md5 des-cbc-crc  
>
>[realms]
>  CERN.CH = {
>    default_domain = cern.ch
>    kdc = cerndc.cern.ch
>  }
>  IPP-GARCHING.MPG.DE = {
>    kdc = kerberos.rzg.mpg.de
>    kdc = kerberos1.rzg.mpg.de
>    kdc = kerberos2.rzg.mpg.de
>    kdc = kerberos3.rzg.mpg.de
>    admin_server = kerberos1.rzg.mpg.de
>  }
>
>[domain_realm]
>  cern.ch = CERN.CH
>  .cern.ch = CERN.CH
>
>  rzg.mpg.de = IPP-GARCHING.MPG.DE
>  .rzg.mpg.de = IPP-GARCHING.MPG.DE
>  ipp.mpg.de = IPP-GARCHING.MPG.DE
>  .ipp.mpg.de = IPP-GARCHING.MPG.DE
>  ipp-hgw.mpg.de = IPP-GARCHING.MPG.DE
>  .ipp-hgw.mpg.de = IPP-GARCHING.MPG.DE
>  ipp-garching.mpg.de = IPP-GARCHING.MPG.DE
>  .ipp-garching.mpg.de = IPP-GARCHING.MPG.DE
>
>[appdefaults]
>  pam = {
>    debug = false
>    ticket_lifetime = 2592000
>    renew_lifetime = 2592000
>    forwardable = true
>    minimum_uid = 100
>    afs_cells = ipp-garching.mpg.de
>    max_timeout = 30
>    timeout_shift = 2
>    initial_timeout = 1
>  }

<=========================================

3. re-start OpenAFS client:
  
>$ sudo service openafs-client restart


Login:

>$ kinit user@CERN.CH     # get kerberos ticket
>$ aklog                  # login to AFS cell


Etc:

Configuration steps 1) and 2) can be done with:
>$ sudo dpkg-reconfigure openafs-client
>$ sudo dpkg-reconfigure krb5-config


References:
  http://akorneev.web.cern.ch/akorneev/howto/openafs.txt
  http://blogs.interdose.com/sebastian/2010/01/31/openafs-client-on-ubuntu-9-10-%E2%80%9Ckarmic-koala%E2%80%9D/
  http://matienzo.org/project/setting-up-umich-afs-on-ubuntu
  http://freecog.net/2007/openafs-ubuntu-feisty

