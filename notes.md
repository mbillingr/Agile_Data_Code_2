Running
=======

```
$> docker build -t agile-data-science-2 .
$> docker run -p 8888:8888 -p 5000:5000 -p 8080:8080 --name ads2 agile-data-science-2
$> docker run -p 8888:8888 -p 5000:5000 -p 8080:8080 -v `pwd`:/root/Agile_Data_Science_2 --name ads2 agile-data-science-2
```

Setup Issues
============

mongodb - spark/hadoop connection not working
---------------------------------------------
Apparently, the jar files in libs/ (PYTHONPATH) were not found.
Copying them to ~/spark/jars seems to have solved the problem.

Airflow
-------
```
$> airflow initdb
```

Daemons
=======

Running MongoDB
---------------
```
$> mongod --fork --logpath /var/log/mongodb.log --config /etc/mongod.conf
```

Running Elastic
---------------
Cannot run as root user.
```
$> su es
$> /root/elasticsearch/bin/elasticsearch -d
$> exit
```

Running Kafka
-------------
```
$> /root/kafka/bin/zookeeper-server-start.sh -daemon /root/kafka/config/zookeeper.properties
$> /root/kafka/bin/kafka-server-start.sh -daemon /root/kafka/config/server.properties
```

Airflow
-------
```
$> airflow webserver -D &
$> airflow scheduler -D &
```

Running Jupyter
---------------
```
$> cd Agile_Data_Code_2
$> jupyter notebook --allow-root
```
