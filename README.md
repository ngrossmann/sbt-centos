## RPM Build Tools for SBT and Native Packager

[SBT Native Packager](http://www.scala-sbt.org/sbt-native-packager/formats/rpm.html)
is a greate tool to build RPMs from your Scala project, but it
depends on the native rpm build tools which are not that easy
to install on a non-rpm based system.

This docker image provides Java 8, sbt, git and everything
needed pre-installed on CentOS 7 and should make it easy to build
RPMs on any system supporting docker.

## Prerequisites

You must have [docker installed](https://docs.docker.com/installation/).
The image doesn't use any fancy features if your distribution's 
repository contains an older version of docker than then
docker.com repositories it may be good enough.

## Usage

If your user is not member of the group docker you need to run
the `docker` commands below with `sudo`.

```
$ docker run -ti --name=mybuild ngrossmann/sbt-centos
[root@bc4b72305a41 /]# git clone https://... build
[root@bc4b72305a41 /]# cd build
[root@bc4b72305a41 build]# sbt rpm:packageBin
...
[root@bc4b72305a41 build]# exit
$ docker cp mybuild:build/target/rpm/RPMS .
```

