
# Big Data DevOps

## Instalacja dystrybucji HDP 2.6

### Wrzuć na maszynę

Lokalnie:
~~~bash
scp -r -P 2222 hdp-centos7-local-prepare.sh root@localhost://root
scp -r -P 2222 hdp-centos7-local-ambari-install.sh root@localhost://root
~~~

AWS:
~~~bash
for i in {1..5..1}; do scp -r hdp-centos7-local-prepare.sh ec2-user@aws${i}://tmp; done
~~~

Własne maszyny HDP:
~~~bash
for i in {1..5..1}; do scp -r hdp-centos7-local-prepare.sh hdp${i}://tmp; done
scp -r hdp-centos7-local-ambari-install.sh hdp1://tmp
~~~


### Przygotowanie maszyn

~~~bash
ssh root@localhost -p 2222

chmod u+x /tmp/hdp-centos7-local-prepare.sh

/tmp/hdp-centos7-local-prepare.sh

reboot
~~~

### Instalacja Ambari

~~~bash
ssh root@localhost -p 2222

chmod u+x /tmp/hdp-centos7-local-ambari-install.sh

/tmp/hdp-centos7-local-ambari-install.sh
~~~