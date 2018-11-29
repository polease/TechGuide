# Tips and Common Issues

## Sample Repository

- <https://github.com/Azure-Samples/service-fabric-dotnet-core-getting-started>
- <https://github.com/Azure-Samples/service-fabric-java-getting-started>

## Connect to a cluster

- Using Service Fabric CLI

```bash
sfctl cluster select --endpoint https://microservicepoc.westus2.cloudapp.azure.com:19080 --pem ./poccert.pem --no-verify
sfctl cluster select --endpoint http://172.30.4.136:19080/
```

- Use Powershell

```powershell
Connect-ServiceFabricCluster 172.30.4.136:19000
```

## View Service Fabric Event Message

Using PerfView with Azure Service Fabric Event Source Messages [link](https://blogs.msdn.microsoft.com/premier_developer/2017/07/05/using-perfview-with-azure-service-fabric-event-source-messages/)

1. Start PerfView with a command line like this: perfview /onlyproviders=*Microsoft-ServiceFabric-Actors
2. You can collect using Collect | Collect | Start Collection. Make sure that the Advanced Options | Additional Providers field contains =*Microsoft-ServiceFabric-Actors When you finish collecting they are viewable under Events

```bash
perfview /onlyproviders=*MyCompany-ServiceCounterApplication-CounterService
```

## Remote Connect to Linux box

```bash
ssh lin@172.30.4.136
```

## NAT for Services on local to Internet

Install [ngrok](https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-windows-amd64.zip)

```bash
ngrok http 172.30.4.136:19080
```

## Docker Run Service Fabric

https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-local-linux-cluster-windows

```bash
docker run -itd -p 19080:19080 -p 20001:20001 --name sfonebox microsoft/service-fabric-onebox
docker exec -it sfonebox bash
```

## Linux Service Fabric Troubleshooting

### System Paths

- View System Log 
```bash
nano /var/log/syslog
```

- Linux app installation path
```bash
/home/sfuser/sfdevcluster/data/_App/_Node_1/
```

- Java path
```bash
/usr/lib/jvm/java-8-openjdk-amd64/bin/java
```

### Linux Java App cann't startup

This is due to the **entryPoint.sh** should be using LF as return line instead of CRLF.


### Turn on Java Logging

Update **entryPoint.sh** file with below custom logging properity file.

```bash
java -Djava.library.path=$LD_LIBRARY_PATH -Djava.util.logging.config.file=logging.properties -jar EmbeddedJettyServer.jar
```

**logging.properties** file:

```bash 
handlers = java.util.logging.FileHandler

java.util.logging.FileHandler.level = ALL
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter

# This value specifies your custom location. You will have to ensure this path has read and write access by the process running the SF Application
java.util.logging.FileHandler.pattern = /tmp/Jetty.0.log
```

## Convert a certificate from PFX to PEM format

```bash
winpty openssl pkcs12 -in linpocvault-linpoccert-20181116.pfx -out poccert.pem -nodes
```
