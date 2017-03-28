# Gitlab ce  + Sonarque + Sonar gitlab plugin  Installation 
## Requiments:
  - OS: linode Centos 7.0 64 bit, 4GB RAM, 3CPUs
  - [Sonarqube 5.6](https://sonarsource.bintray.com/Distribution/sonarqube/sonarqube-5.6.6.zip)
  - [Gitlab ce version 8.17.4](https://about.gitlab.com/downloads/#centos7)
  - [Sonar gitlab plugin 1.7](https://github.com/gabrie-allaigre/sonar-gitlab-plugin)
   
## 1.Install Sonarqube
Sonarqube requires minimum 2G RAM for installing and running.

**1.1. Install java 1.8**

 - [x] Download the file: jdk-8u121-linux-x64.rpm here [Java JDK 1.8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)
 - [x] After we go to above link, click on "Accept License Agreement" and copy the download url of the file: **jdk-8u121-linux-x64.rpm**
- [x] Install Java jdk with rpm by running following commands as **root**
```
  cd /tmp/
  wget http://download.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.rpm
  rpm -ivh jdk-8u121-linux-x64.rpm
```
- [x] After running above commands, Java jdk 1.8 will be installed

**1.2. Install Sonarqube**

 - [x] [Download sonarqube 5.6](https://sonarsource.bintray.com/Distribution/sonarqube/sonarqube-5.6.6.zip)
 - [x] Extract file zip sonarqube-5.6.6.zip
 - [x] Change database connection settings, [check here](https://docs.sonarqube.org/display/SONAR/Installing+the+Server#InstallingtheServer-installingDatabaseInstallingtheDatabase)
 - [x] Run command to start Sonarqube
 
 You can find settings on the file : /var/www/sonarqube-5.6.6/conf/sonar.properties

>sonar.jdbc.username=sonarqube <br>
>sonar.jdbc.password=mypassword <br>
>sonar.jdbc.url=jdbc:postgresql://localhost/sonarqube

 Commands:
 ```
 cd /var/www/
 wget https://sonarsource.bintray.com/Distribution/sonarqube/sonarqube-5.6.6.zip
 unzip sonarqube-5.6.6.zip
 #after changing db setting on sonar.properties 
 bash /var/www/sonarqube-5.6.6/bin/linux-x86-64/sonar.sh start
 ```
 - [x] Sonarqube should be started now
 
 Now go to the url : http://localhost:9000 you will see the homepage of sonarque
 
**1.3. Install SonarPHP plugins **

The SonarPHP plugins will analyze your php code and display the result on a statistic.   
You can find the plugins for your programming language [here](https://docs.sonarqube.org/display/PLUG/Plugin+Library)

Commands :
```
wget -P /var/www/sonarqube-5.6.6/extensions/plugins/ https://sonarsource.bintray.com/Distribution/sonar-php-plugin/sonar-php-plugin-2.10.0.2087.jar
bash /var/www/sonarqube-5.6.6/bin/linux-x86-64/sonar.sh restart
```

**1.4. Install and run sonarqube scanner**
- [x] Download the sonarqube scanner zip file [here](https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.0.0.702-linux.zip)
- [x] Extract file sonar-scanner-cli-3.0.0.702-linux.zip
- [x] Change sonarqube scanner configuration 
- [x] Declare configurations for sonarqube scanner on your php project
- [x] Start running scanner

Commands :
```
wget -P /var/www/ https://sonarsource.bintray.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-3.0.0.702-linux.zip
```
Change config file: /var/www/sonar-scanner-3.0.0.702-linux/conf/sonar-scanner.properties
On this file you need to correct the following information: database user, database pass and sonarqube url.

Create new file: sonar-project.properties in the root folder of php project. Please download [sonarqube sample projects](https://github.com/SonarSource/sonar-examples) for more details. 
>sonar.projectKey=my:project <br>
>sonar.projectName=My project <br>
>sonar.projectVersion=1.0 <br>
>sonar.sources=.

Then go to the root folder of project and run :

```
/var/www/sonar-scanner-3.0.0.702-linux/bin/sonar-scanner
```

Go to the http://ip:9000 you should see the new project on sonarqube  now.

## 2.Install Gitlab

> Install gitlab on centos 7

## 3.Install sonar gitlab plugin


## 4.References

1. https://docs.sonarqube.org/display/SONAR/Documentation
2. https://about.gitlab.com/downloads/#centos7
3. https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner
4. https://github.com/SonarSource/sonar-examples
5. https://github.com/gabrie-allaigre/sonar-gitlab-plugin
