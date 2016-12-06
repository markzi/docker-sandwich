# Docker

## Build an image from a Dockerfile

```
docker build -t ibm:db2-express-c .
```

## Run a image in a new container
```
docker run -dt \
  -p 50000:50000 \
  --name db2 \
  -e DB2INST1_PASSWORD=db2inst1-pwd \
  -e LICENSE=accept -v /tmp:/share \
  ibm:db2-express-c db2start
```
```
-d as daemon
-t tty shell??
-p map container port 50000 to host machine 50000
-name name the container db2
-e set environment variable DB2INST1_PASSWORD to db2inst1-pwd
-e set environment variable LICENSE to accept
-v mount volume /tmp to host machine /share
image
command
```

## List containers
```
docker ps
```

## Stop one or more running containers
```
docker stop <CONTAINER_ID>
```

## start/stop instance
```
su - db2inst1
db2start
db2sampl
```

# Database

## Creating the DHPI04 DB and updating the docker image from within a running container

1. Create the DB. Execute this in the container
```
su - db2inst1
db2 create db DHPI04
```

2. Exit container and then find the CONTAINER ID
```
docker ps -a
```

3. Update image from the container
```
docker commit -m "Created DHPI04 database" -a "Mark Homan" <CONTAINER_ID> ibm:db2-express-c
```

# Puppet

## Install Puppet Agent

### Enable the official Puppet Labs collection repository with this command:
```
sudo rpm -ivh https://yum.puppetlabs.com/puppetlabs-release-pc1-el-7.noarch.rpm
```

### Install the puppet-agent package:
```
sudo yum -y install puppet-agent
```

### Now that the Puppet agent is installed, start it with this command:
```
sudo /opt/puppetlabs/bin/puppet resource service puppet ensure=running enable=true
```
