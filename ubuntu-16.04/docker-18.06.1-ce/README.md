# Microsoft VSTS-Agent
## Based on microsoft/vsts-agent:ubuntu-16.04-docker-18.06.1-ce-standard

**Including:**
* Microsoft VSTS Agent 2.174.1
* .NET Core SDK 2.2.402
* GitVersion 5.0.1
* VIM Editor
* Pact 1.70.2
* Mongodb shell 2.6.10
* Clair-scanner 12


**GitVersion**

Contains the .NET Core version of GitVersion 5.0.1

Application is installed in the following folder: /opt/GitVersion/GitVersion.dll

You can use GitVersion by just type **dotnet /opt/GitVersion/GitVersion.dll** in the folder which contains a git repository.
More information about GitVersion can be found [here](https://gitversion.readthedocs.io/en/latest/)


**Pact**

Application is installed in the following folder: /opt/pact

More information about Pact can be found [here](https://github.com/pact-foundation/pact-ruby-standalone/releases)


**MongoDB Shell**

Application can be used by typing 'mongo'

More information about MongoDB shell can be found [here](https://docs.mongodb.com/manual/mongo/index.html)


**Clair-scanner v10**

Application is installed in the following folder: /opt/clair-scanner/clair-scanner

More information about clair-scanner can be found [here](https://github.com/arminc/clair-scanner)
