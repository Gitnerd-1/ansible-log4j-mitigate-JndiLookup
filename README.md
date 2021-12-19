# Ansible playbook to mitigate log4j JndiLookup.class

Almost all versions of Log4j are vulnerable, starting from 2.0-beta9 to 2.14.1. The simplest and most effective protection method is to install the most recent version of the library, 2.16.0 (at time of writing). You can download it on the project page.

If for some reason updating the library is not possible, the adviced recommendation is to use one of the mitigation methods. To protect all releases of Log4j (from 2.0-beta9 to 2.14.1), the library developers recommend removing the JndiLookup class from the classpath: `zip -q -d log4j-core – *. Jar org / apache / logging / log4j / core / lookup / JndiLookup .class.`

This playbook can help you accomplish that for all Linux systems, if yoy are using Ansible. The playbook can list and remove vulnerable '.jar' files containing _org/apache/logging/log4j/core/lookup/JndiLookup.class_ from '*.jar' files on the local filesystem.


### List all jar files containing vulnerable JndiLookup.class

```
$ ansible-playbook log4j-mitigate.yml
```
  
### Remove all JndiClasses form found jar files

```
$ ansible-playbook log4j-mitigate.yml -e "remove_class=true"
``` 
  
