# Gitlab ce  + Sonarque + Sonar gitlab plugin  Installation 
##0. Requiments:
  - OS: linode Centos 7.0 64 bit, 4GB RAM, 3CPUs
  - [Sonarqube 5.6](https://sonarsource.bintray.com/Distribution/sonarqube/sonarqube-5.6.6.zip)
  - [Gitlab ce version 8.17.4](https://about.gitlab.com/downloads/#centos7)
  - [Sonar gitlab plugin 1.7](https://github.com/gabrie-allaigre/sonar-gitlab-plugin)
   
##1. Install Sonarqube
> Sonarqube requires minimum 2G RAM for installing and running.

1.1. Install java 1.8
 - [x] Download the file: jdk-8u121-linux-x64.rpm here [Java JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
 - [x] After we go to above link, click on "Accept License Agreement" and copy the download url of the file: **jdk-8u121-linux-x64.rpm**
- [x] Install Java jdk with rpm by running following commands as **root**
```
  cd /tmp/
  wget http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.rpm
  rpm -ivh jdk-8u121-linux-x64.rpm
```
- [x] After running above commands, Java jdk 1.8 will be installed
1.2. Install Sonarqube
 - [x] 

1.3. Install Sonarqube plugins

1.4. Usage of sonarqube scanner


##2. Install Gitlab

> Install gitlab on centos 7

##3. Install sonar gitlab plugin


##4. References

1. https://docs.sonarqube.org/display/SONAR/Documentation
2. https://about.gitlab.com/downloads/#centos7
3. 
4. 