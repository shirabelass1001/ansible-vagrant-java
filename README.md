# ansible-vagrant-java


## Please prepare in advance

```$ brew install ansible```

```$ brew cask install vagrant```

```$ brew cask install virtualbox```

## clone

```git clone  https://github.com/shirabelass1001/ansible-vagrant-java.git```

## run

```$ vagrant up```

## check

[http://192.168.33.10:8080/sample/](http://192.168.33.10:8080/sample/)

## customize

If you want to change war file in /www/tomcat/webapps

### 1. change file name

before
> ```sample-1.0.war```

after
> ```yourfilename.war```

### 2. edit main.yml

```$ cd /roles/tomcat/tasks```

```$ vi main.yml```

before
> ```- name: symbolic link to war file
  file: src=/var/www/tomcat/webapps/sample-1.0.war dest=/usr/share/tomcat/webapps/sample.war state=link force=yes```

after
> ```- name: symbolic link to war file
  file: src=/var/www/tomcat/webapps/yourfilename.war dest=/usr/share/tomcat/webapps/sample.war state=link force=yes```

### 3. edit context.xml
before
> ```<Context path="" docBase="sample" allowLinking="true" debug="0" reloadable="true" crossContext="true">```

after
> ```<Context path="" docBase="yourfilename" allowLinking="true" debug="0" reloadable="true" crossContext="true">```
