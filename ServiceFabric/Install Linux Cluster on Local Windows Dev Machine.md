# Install Linux Cluster on Local Windows Dev Machine

## Install Linux VM

### Enable Hyper-V

Hyper-V should be enabled to intall the ubuntu 
<https://docs.microsoft.com/en-us/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v>

### Download Ubuntu ISO Image

<http://releases.ubuntu.com/16.04/>

## Install Service Fabric on Linux

Following steps are referencing this guide here.
<https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-get-started-linux>

After linux VM installed, run following command from linux terminal.

``` Bash
sudo apt-get update
sudo apt-get install curl
sudo curl -s https://raw.githubusercontent.com/Azure/service-fabric-scripts-and-templates/master/scripts/SetupServiceFabric/SetupServiceFabric.sh | sudo bash
sudo /opt/microsoft/sdk/servicefabric/common/clustersetup/devclustersetup.sh
```

If you would like to use remote terminal, install openSSH within linux terminal as well.
``` Bash
sudo apt install openssh-server
```

### Install Java Runtime

Run following bash command

``` Bash
sudo apt-get install openjdk-8-jdk-headless
sudo apt-get install gradle
```

### Start Using Service Fabric

Now service fabric should be up and running, use <http://[YOUR_LINUX_IP]:19080/Explorer/index.html#> to view service fabric mangement tool.
 
## Install Service Fabric CLI

### Install Python 3.7

https://www.python.org/downloads/release/python-370/

### Install Service Fabric CLI from Pip

``` Bash
pip install sfctl
```

if you would like to access Azure Service Fabric, install the **Azure CLI** from here <https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest>

### Setup Eclipse Plug-in

Follow this article to setup eclipse plugin
https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-get-started-eclipse
