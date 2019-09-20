FROM microsoft/vsts-agent:ubuntu-16.04-docker-18.06.1-ce-standard

MAINTAINER Jean-Pierre Broeders <github@freelyit.nl>

# Download the Microsoft repository GPG keys
RUN wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
RUN dpkg -i packages-microsoft-prod.deb

# Update all existing packages to the latest version
RUN apt-get update

# Install latest Microsoft vsts agent
RUN set -x \
 && curl -fSL https://vstsagentpackage.azureedge.net/agent/2.158.0/vsts-agent-linux-x64-2.158.0.tar.gz -o agent.tgz \
 && mkdir agent \
 && cd agent \
 && tar -xz --no-same-owner -f ../agent.tgz \
 && cd .. \
 && rm agent.tgz

# Install GitVersion to /opt/GitVersion folder
RUN apt-get install -y unzip mono-runtime libmono-system-core4.0-cil libgit2-24 && \
    curl -L -o /tmp/GitVersion_5.0.1.zip https://github.com/GitTools/GitVersion/releases/download/5.0.1/GitVersion-bin-corefx-v5.0.1.zip && \
    unzip -d /opt/GitVersion /tmp/GitVersion_5.0.1.zip && \
    rm /tmp/GitVersion_5.0.1.zip && \
    echo '<configuration><dllmap os="linux" cpu="x86-64" wordsize="64" dll="git2-baa87df" target="/usr/lib/x86_64-linux-gnu/libgit2.so.24" /></configuration>' > \
    /opt/GitVersion/LibGit2Sharp.dll.config
 
# Install Extra packages
RUN apt-get install \
    vim \
	mongodb-clients
	
# Install Pact
RUN curl -L -o /tmp/pact-1.70.2-linux-x86_64.tar.gz https://github.com/pact-foundation/pact-ruby-standalone/releases/download/v1.70.2/pact-1.70.2-linux-x86_64.tar.gz && \
	tar -xvf /tmp/pact-1.70.2-linux-x86_64.tar.gz -C /opt && \
    rm /tmp/pact-1.70.2-linux-x86_64.tar.gz

# Install Clair-scanner v10
RUN mkdir /opt/clair-scanner \
	&& curl -L -o /opt/clair-scanner/clair-scanner https://github.com/arminc/clair-scanner/releases/download/v12/clair-scanner_linux_amd64 && chmod +x /opt/clair-scanner/clair-scanner

# Install PowerShell
RUN apt-get install -y powershell

# Install .NET Core SDK 2.2
RUN apt-get install -y --no-install-recommends \
    apt-transport-https \
    dotnet-sdk-2.2 \
	&& rm -rf /var/lib/apt/lists/* \
	&& rm -rf /etc/apt/sources.list.d/*
RUN dotnet --info
ENV dotnet=/usr/bin/dotnet
 
COPY ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]
