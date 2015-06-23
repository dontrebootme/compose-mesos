# docker-compose-mesos
## docker-compose
### Usage
```
➜  docker-compose-mesos (master) ✗ docker-compose up -d
Creating bifigmesos_zk1_1...
Creating bifigmesos_mesos1_1...
Creating bifigmesos_chronos_1...
Creating bifigmesos_marathon_1...
Creating bifigmesos_slave1_1...
Creating bifigmesos_slave2_1...
Creating bifigmesos_slave3_1...
➜  bi-fig-mesos (master) ✗ docker ps
CONTAINER ID        IMAGE                                 COMMAND                CREATED             STATUS              PORTS                          NAMES
d62c041b1e2b        redjack/mesos-slave:0.21.0            "mesos-slave"          24 seconds ago      Up 2 seconds        0.0.0.0:5053->5051/tcp         bifigmesos_slave3_1
d6693618515f        redjack/mesos-slave:0.21.0            "mesos-slave"          25 seconds ago      Up 3 seconds        0.0.0.0:5052->5051/tcp         bifigmesos_slave2_1
3834bef197ac        redjack/mesos-slave:0.21.0            "mesos-slave"          26 seconds ago      Up 3 seconds        0.0.0.0:5051->5051/tcp         bifigmesos_slave1_1
a3797909b3aa        mesosphere/marathon:v0.7.6            "./bin/start --maste   26 seconds ago      Up 4 seconds        0.0.0.0:8080->8080/tcp         bifigmesos_marathon_1
db7b40e0d82f        tomaskral/chronos:2.3.0-mesos0.21.0   "/usr/local/bin/chro   27 seconds ago      Up 5 seconds        0.0.0.0:4400->8080/tcp         bifigmesos_chronos_1
2f45d98e38e3        redjack/mesos-master:0.21.0           "mesos-master"         27 seconds ago      Up 5 seconds        0.0.0.0:5050->5050/tcp         bifigmesos_mesos1_1
13fd357f7c24        jplock/zookeeper:3.4.6                "/opt/zookeeper/bin/   28 seconds ago      Up 6 seconds        2181/tcp, 2888/tcp, 3888/tcp   bifigmesos_zk1_1
➜  bi-fig-mesos (master) ✗ curl -X POST -H "Content-Type: application/json" http://192.168.59.103:8080/v2/apps -d@demo-app.json
{"id":"/inky","cmd":null,"args":["hello"],"user":null,"env":{},"instances":12,"cpus":0.2,"mem":32.0,"disk":0.0,"executor":"","constraints":[],"uris":[],"storeUrls":[],"ports":[],"requirePorts":false,"backoffSeconds":1,"backoffFactor":1.15,"container":{"type":"DOCKER","volumes":[],"docker":{"image":"mesosphere/inky","network":null,"portMappings":null,"privileged":false,"parameters":{}}},"healthChecks":[],"dependencies":[],"upgradeStrategy":{"minimumHealthCapacity":1.0},"version":"2015-02-19T04:23:22.020Z"}%
```

### Deployments
```
curl -X POST -H "Content-Type: application/json" http://192.168.59.103:8080/v2/apps -d@demo-app.json
curl -X POST -H "Content-Type: application/json" http://192.168.59.103:8080/v2/apps -d@demo-python.json
```

### Mesos
``` for anyone using OSX, get the IP of your docker host using 'boot2docker ip' ```

http://192.168.59.103:5050

### Marathon
``` for anyone using OSX, get the IP of your docker host using 'boot2docker ip' ```

http://192.168.59.103:8080

### Chronos
``` for anyone using OSX, get the IP of your docker host using 'boot2docker ip' ```

http://192.168.59.103:4400

### Cleanup
```
./cleanup
```
