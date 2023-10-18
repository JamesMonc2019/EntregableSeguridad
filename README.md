# VulnerableApp

[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=TsuyoshiUshio_VulnerableApp&metric=alert_status)](https://sonarcloud.io/dashboard?id=TsuyoshiUshio_VulnerableApp)

This application is created for testing the security scan for .NET. Also this repo include a Dockerfile for Windows Container.

.NET Framework 4.5 with downgrading to the ASP.NET MVC 5.1 nuget package. It includes vulnerability of this. 

* [Microsoft Security Bulletin MS14-059 - Important](https://docs.microsoft.com/en-us/security-updates/securitybulletins/2014/ms14-059?fbclid=IwAR0xi1tpueLDl3V_GwBzn_5PuvW2yQM74_KPv4dL5C8YpNs8fVmT1UThy5I)

# How to create a docker image 

## Prerequisite 

* Docker for windows 
* Docker for windows swiched to windows container

## Build docker file

## Publish 

* Go to "Publish" on your Visual Studio 2017 
* Publish FolderProfile. It create an artifact for bin\Release\Publish

## Build 

Build an image of docker. Replace the `<<docker image name>>`.

```
cd VulnerableApplication
docker build -t <<docker image name>> . 
```

It pack the artifact into the container. The image include ASP.NET with DotNet farmework 4.7. 

## Run 

Now you can run the container. It exposes 80 port to access the web application. 

```
docker run <<docker image name>>
```

Get the IP address of the docker container 

```
 docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" <<docker image name>>
```

access the IP address with your browser. then you can see the website. 



