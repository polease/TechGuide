# Setup Local Environment with Visual Studio Code

This article is referencing [document](https://docs.microsoft.com/en-us/azure/service-fabric/service-fabric-get-started-vs-code)

## Installation Steps

- [Visual Studio Code](https://code.visualstudio.com/)
- [Node.js](https://nodejs.org/)
- [Git](https://git-scm.com/)
- [Service Fabric SDK](https://www.microsoft.com/web/handlers/webpi.ashx?command=getinstallerredirect&appid=MicrosoftAzure-ServiceFabric-CoreSDK)
- Yeoman Generator
    ```bash
    npm install -g yo
    npm install -g generator-azuresfjava
    npm install -g generator-azuresfcsharp
    npm install -g generator-azuresfcontainer
    npm install -g generator-azuresfguest
    ```

## Enable Java

- [Java SDK version 1.8](https://repos.azul.com/azure-only/zulu/packages/zulu-8/8u192/zulu-8-azure-jdk_8.33.0.1-8.0.192-win_x64.zip)
- [Chocolatey](https://chocolatey.org/)
- Gradle
    ```bash
    choco install gradle
    ```

## Install Service Fabric CLI

### Install Python 3.7

https://www.python.org/downloads/release/python-370/

### Install Service Fabric CLI from Pip

``` Bash
pip install sfctl
```

if you would like to access Azure Service Fabric, install the **Azure CLI** from here <https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-windows?view=azure-cli-latest>