

- Setup Hadoop Cluster on Single Node
- Download Hadoop Extract in the directory `/home/nikx/hadoop`
  - [Download Hadoop](https://hadoop.apache.org/releases.html)
- Download JAVA (1.8)
  - [Java Releases](https://www.oracle.com/in/java/technologies/downloads/)
  - [Java 1.8](https://download.oracle.com/otn/java/jdk/8u361-b09/0ae14417abb444ebb02b9815e2103550/jdk-8u361-linux-x64.tar.gz?AuthParam=1679295844_f27bec1347760251d03628daf9146c35)
  - Extract JAR file in location `/home/nikx/java/202`
- Setup Configs to make hadoop aware of the single node
  - All configs locations are `/home/nikx/hadoop/etc`
  - Setup `hadoop-env.sh`
  ```bash
  export JAVA_HOME=/home/nikx/java/202
  ```
  - Configure `core-site.xml`
  ```xml
  <configuration>
    <property>
      <name>fs.default.name</name><value>hdfs://localhost:9000</value>
    </property>
    <property>
      <name>hadoop.tmp.dir</name>
      <value>/home/nikx/src/temp</value>
    </property>
  </configuration>
  ```



---
- [Reference - 1](https://data-flair.training/blogs/install-hadoop-on-single-machine/)
