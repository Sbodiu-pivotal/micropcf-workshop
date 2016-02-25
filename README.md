# micropcf-workshop
Getting Started with microPCF


micropcf
>MicroPCF is the simplest way to get a complete Cloud Foundry on a single machine

Get in touch with team [GitHub](https://github.com/pivotal-cf/micropcf) [Slack](https://pivotal.slack.com/messages/micropcf/)


Setup
You can set up micropcf to easily:

```
    cd micropcf-workshop
    wget https://github.com/pivotal-cf/micropcf/releases/download/v0.6.0/micropcf-v0.6.0.zip
    unzip micropcf-v0.6.0.zip
    cd micropcf-v0.6.0
```

Now you need to download 4 GB box, which will take a while

```
    vagrant up
    
```

Once you got successfully you can create a bash script for ease of use

```
    #!/bin/bash
    cf api api.local.micropcf.io --skip-ssl-validation
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

Bonus install micropcf base without service brokers:

```
    cd micropcf-workshop
    wget https://micropcf.s3.amazonaws.com/releases/base-v0.6.0.zip
    unzip base-*
    cd base-*
    vagrant up
```    


Troubleshooting:
if you have trouble with networking you can follow belloe guides
    
https://passingcuriosity.com/2013/dnsmasq-dev-osx/

Linux:
    sudo invoke-rc.d dnsmasq restart