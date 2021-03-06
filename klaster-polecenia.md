
# Usuwanie poprzednich wpisów

~~~shell
for i in {1..5..1}; do ssh-keygen -f "/home/radek/.ssh/known_hosts" -R hdp${i}; done
for i in {1..5..1}; do ssh-keygen -f "/home/radek/.ssh/known_hosts" -R hdpoc${i}; done
for i in {1..5..1}; do ssh-keygen -f "/home/radek/.ssh/known_hosts" -R aws${i}; done
~~~

# Uptime
~~~shell
for i in {1..5..1}; do ssh hdp${i} uptime; done
for i in {1..5..1}; do ssh aws${i} uptime; done
~~~

# Usuwanie adresów ip z known hosts

~~~
ssh-keygen -R 176.119.46.247
~~~

# Połączenie się do maszyn

~~~shell
cssh hdp{1..5}
cssh aws{1..5}
~~~

# Lista użytkowników
~~~shell
for i in `cat /tmp/users.txt`; do echo ${i}; done
~~~

# Tworzenie użytkownika
~~~shell
for i in `cat /tmp/users.txt`; do adduser ${i} ; done
for i in `cat /tmp/users.txt`; do echo "${i}:${i}" | chpasswd ; done
~~~

# HDFS - create
~~~shell
for i in `cat /tmp/users.txt`; do hdfs dfs -mkdir /user/${i}; done
for i in `cat /tmp/users.txt`; do hdfs dfs -chown ${i} /user/${i}; done
~~~

# HDFS - snapshot
~~~shell
for i in `cat /tmp/users.txt`; do hdfs dfsadmin -allowsnapshot /user/${i}/snap; done
~~~




# HDFS - delete
~~~shell
for i in `cat /tmp/users.txt`; do hdfs dfs -rm -r -skipTrash /user/${i}; done
~~~

# Usuwanie użytkowników
~~~shell
for i in `cat /tmp/users.txt`; do userdel -r  ${i} ; done
~~~

# Czyszczenie Hive'a
~~~shell
hdfs dfs -ls /warehouse/tablespace/managed/hive
hdfs dfs -ls /warehouse/tablespace/external/hive

for i in `cat /tmp/users.txt`; do hdfs dfs -rm -r -skipTrash /warehouse/tablespace/external/hive/${i}; done
for i in `cat /tmp/users.txt`; do hdfs dfs -rm -r -skipTrash /warehouse/tablespace/external/hive/${i}.db; done
~~~