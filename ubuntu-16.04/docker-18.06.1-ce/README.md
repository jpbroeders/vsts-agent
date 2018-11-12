# Microsoft VSTS-Agent
## Based on microsoft/vsts-agent:ubuntu-16.04-docker-18.06.1-ce-standard


**Including:**
* GitVersion 4.0.0
* VIM Editor
* Pact 1.61.2
* Mongodb shell 2.6.10


**GitVersion**

Contains the .NET Core version of GitVersion 4.0.0

Application is installed in the following folder: /opt/GitVersion/GitVersion.dll

You can use GitVersion by just type **dotnet /opt/GitVersion/GitVersion.dll** in the folder which contains a git repository.
More information about GitVersion can be found [here](https://gitversion.readthedocs.io/en/latest/)


**Pact**

Application is installed in the following folder: /opt/pact

More information about Pact can be found [here](https://github.com/pact-foundation/pact-ruby-standalone/releases)


**MongoDB Shell**

Application can be used by typing 'mongo'
More information about [MongoDB shell](https://docs.mongodb.com/manual/mongo/index.html)