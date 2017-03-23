# Prerequisites

# How to run ADOP on OpenShift

# Errors identified

## Proxy
This container can't be launched and issues the following error: <br>
``cp: target '/usr/share/nginx/html/' is not a directory``

## LDAP
### ldap
WORKS
### ldap-phpadmin
ldap-phpadmin can't connect directly to ldap server using hostname. However, reconfiguring ``/etc/phpldapadmin/config.php`` and set the IP address of the ldap-server container instead of its hostname seems to fix the problem. See example below: <br><br>

``
<?php                                                                             $servers = new Datastore();                                                                      $servers->newServer('ldap_pla');                                                  $servers->setValue('server','name','ldap');                                       $servers->setValue('server','``__IP_ADDRESS__``','ldap');                                       $servers->setValue('server','port','389');                                        $servers->setValue('server','base',array('dc=ldap,dc=example,dc=com'));           $servers->setValue('login','auth_type','cookie');                                 $servers->setValue('login','bind_id','cn=admin,dc=ldap,dc=example,dc=com');       $servers->setValue('server','tls',false);                                         ?>  
``

### ldap-ltb
Logs display the following message: <br>
``AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 10.128.0.42. Set the 'ServerName' directive globally to suppress this message``

## Gerrit
### gerrit-mysql
### gerrit
Once launched, Gerrit display the following message each 10 seconds: <br>
``Gerrit unavailable, sleeping for 10`` <br>
Content of ``gc_log`` file: <br>
``2017-03-22 13:53:29,570] INFO  : Ignoring missing gc schedule configuration`` <br>
``httpd_log`` & ``sshd_log`` do not display any errors <br>

## Sensu
### sensu-redis
WORKS
### sensu-rabbitmq
WORKS
### sensu-api
``{"timestamp":"2017-03-23T08:51:58.830830+0000","level":"error","message":"redis connection error","error":"unable to connect to redis server"}
{"timestamp":"2017-03-23T08:51:59.022461+0000","level":"error","message":"[amqp] Detected TCP connection failure: Errno::EHOSTUNREACH"}``
### sensu-server
``{"timestamp":"2017-03-23T08:52:01.840097+0000","level":"error","message":"redis connection error","error":"unable to connect to redis server"}
{"timestamp":"2017-03-23T08:52:02.028845+0000","level":"error","message":"[amqp] Detected TCP connection failure: Errno::EHOSTUNREACH"}``
### sensu-client
### sensu-uchiwa
``{"timestamp":"2017-03-23T09:15:13.41385771Z","level":"warn","message":"GET http://sensu-api:4567/stashes returned: Get http://sensu-api:4567/stashes: dial tcp 172.30.201.20:4567: getsockopt: no route to host"}
{"timestamp":"2017-03-23T09:15:13.413886253Z","level":"warn","message":"Connection failed to the datacenter Sensu"}``

Error identified:
* Sonar
Error identified:
* Jenkins
Error identified:
* Selenium
Error identified:
* Nexus
Error identified:


# TODO

* Identify Required parameters
* Write parameters' description