# PCFDev Workshop
Getting Started with PCFDev

>PCFDev is the simplest way to get a complete Cloud Foundry on a single machine

Get in touch with team [GitHub](https://github.com/pivotal-cf/pcfdev) [Slack](https://pivotal.slack.com/messages/pcfdev/)

Setup
You can set up pcfdev to easily:

Login to https://network.pivotal.io/products/pcfdev#/releases/1710 and download pcfdev-v0.15.0

Now you need to download 4 GB box, which will take a while

```
unzip pcfdev-*
cd pcfdev
```    

By default, the PCFDev VM will only start with up to 4GB of total memory, it is recommended that you start the VM with at least 8GB of memory:  
  
```    
VM_MEMORY=8192 ./start-osx
```

Once you got successfully you can create a bash script for ease of use

```
#!/bin/bash
cf api api.local.pcfdev.io --skip-ssl-validation
cf login -u admin -p admin
```

Test 1st spring-boot app

```
cd micropcf-workshop
curl https://start.spring.io/starter.tgz \
-d style=web -d name=resource | tar -xzvf -
mvn package
java -jar target/demo-0.0.1-SNAPSHOT.jar
```

Done

alternatively you can use the latest Atlas release

```
vagrant init pcfdev/pcfdev; vagrant up --provider virtualbox
```

Next:

Install new releases of java buildpack (offline) e.g. 1.8.0_91-unlimited-crypto

```
wget https://github.com/cloudfoundry/java-buildpack/releases/download/v3.7.1/java-buildpack-offline-v3.7.1.zip
cf update-buildpack java_buildpack -p java-buildpack-offline-*
```
    

Follow instructions to setup [Spring Cloud Services](https://github.com/dave-malone/pcfdev-spring-cloud-services)

Troubleshooting:
if you have trouble with networking you can follow belloe guides
    
https://passingcuriosity.com/2013/dnsmasq-dev-osx/

https://docs.pivotal.io/pcf-dev/work-offline.html

Linux:
    sudo invoke-rc.d dnsmasq restart
