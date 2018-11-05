FROM microsoft/vsts-agent:ubuntu-16.04-docker-18.06.1-ce-standard

MAINTAINER Jean-Pierre Broeders <github@freelyit.nl>

RUN set -x \
 && curl -fSL https://vstsagentpackage.azureedge.net/agent/2.140.2/vsts-agent-linux-x64-2.140.2.tar.gz -o agent.tgz \
 && mkdir agent \
 && cd agent \
 && tar -xz --no-same-owner -f ../agent.tgz \
 && cd .. \
 && rm agent.tgz

# Install GitVersion to /opt/GitVersion folder
RUN apt-get update && apt-get install -y unzip mono-runtime libmono-system-core4.0-cil libgit2-24 && \
    curl -L -o /tmp/GitVersion_4.0.0.zip https://github.com/GitTools/GitVersion/releases/download/v4.0.0/GitVersion-bin-coreclr-v4.0.0.zip && \
    unzip -d /opt/GitVersion /tmp/GitVersion_4.0.0.zip && \
    rm /tmp/GitVersion_4.0.0.zip && \
    echo '<configuration><dllmap os="linux" cpu="x86-64" wordsize="64" dll="git2-baa87df" target="/usr/lib/x86_64-linux-gnu/libgit2.so.24" /></configuration>' > \
    /opt/GitVersion/LibGit2Sharp.dll.config
 
COPY ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]
