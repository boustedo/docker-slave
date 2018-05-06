FROM openjdk:8-jdk-windowsservercore-ltsc2016

SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

ENV JENKINS_AGENT_REMOTE_VERSION 3.20
ENV JENKINS_AGENT_WORKDIR C:\\agent

RUN $url = ('https://repo.jenkins-ci.org/public/org/jenkins-ci/main/remoting/{0}/remoting-{0}.jar' -f $env:JENKINS_AGENT_REMOTE_VERSION); \
	Write-Host ('Downloading {0} ...' -f $url); \
    Invoke-WebRequest -Uri $url -OutFile 'C:\\slave.jar';

RUN mkdir -p $env:JENKINS_AGENT_WORKDIR

VOLUME ${JENKINS_AGENT_WORKDIR}
WORKDIR ${JENKINS_AGENT_WORKDIR}