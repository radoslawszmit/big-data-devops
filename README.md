# big-data-devops

Instalacja:
~~~bash
scp -r -P 2222 hdp-centos7-local-prepare.sh root@localhost://root
scp -r -P 2222 hdp-centos7-local-ambari-install.sh root@localhost://root

ssh root@localhost -p 2222

chmod u+x hdp-centos7-local-prepare.sh
chmod u+x hdp-centos7-local-ambari-install.sh

./hdp-centos7-local-install.sh
./hdp-centos7-local-ambari-install.sh
~~~