# H2O

Repository based on https://github.com/h2oai/h2o-3/

This repository is used to build h2odriver.jar for TAP purposes. This driver is secured by Basic Authentication.

## Changes

### Basic Authentication

This is feature added by TAP team to base h2o code. To run h2o on YARN with Basic Auth enabled you need to use ```-username``` and ```-password``` parameters. For instance:
```
hadoop jar h2odriver.jar -username giovanni -password giovanni1 -mapperXmx 512m -nodes 4 -driverif 10.0.4.4 -driverport 54310 -jobname h2o_1 -output /tmp/h2o_1 -notify /tmp/h2o_1_ui -disown
```

## Building h2o driver

Prerequisities (ubuntu):
```
apt-get update
apt-get install -y npm
apt-get install -y nodejs
ln -s `which nodejs` /usr/bin/node
apt-get install -y python-pip
pip install tabulate
apt-get install -y r-base
```

Command:
```
export BUILD_HADOOP=1; ./gradlew build -x test
```

Jar will be located here:
```
h2o-hadoop/h2o-cdh5.4.2-assembly/build/libs/h2odriver.jar
```
