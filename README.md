# Confluent Kafka Playbook
This playbook will install confluent kafka into 3 cluster nodes.
Each node will contain one kafka broker and one zookeeper instance and all of them are synchronized.

For the installation, I will use kafka from https://www.confluent.io, or for more clarity I will call it as confluent kafka.
The confluent itself provides two version, enterprise and open source. This playbook will use the latter version, which is an open source one.

_Note: this playbook only works in Redhat/CentOS 7_

# Playbook Structure
The playbook only contains one role, which is `confluent-kafka`. Basically this roles will install and configure 4 services:
* Zookeeper
* Apache Kafka
* Schema Registry
* REST Proxy

The roles itself will automatically install `open-jdk-8` as well.
You can disable the java installation, if you already installed JDK in your target machine, by setting variable `java_install` 
into `false` inside `roles/confluent-kafka/defaults/main.yml`.

# Registering Hosts for Clustering
Because some setup need to be align with properties configuration, there are some tricks to get all hosts into ansible variables.
For example, in `server.properties` there are some configuration to list all zookeeper instances. To address this configuration challanges,
I set up a group called `kafka_broker_nodes`, which contains the 3 nodes to be configured. 

Please take a note with `ansible_host` variable that are listed in all nodes. This variable values will be used by the playbook to be manipulated
via Jinja filter. Therefore, we can trick the properties configuration for all the services.

# Execute

     // make sure you point to the correct host. See hosts files.
     ansible-playbook site.yml -i hosts_local


# Reference
https://docs.confluent.io/current/installation/installing_cp.html