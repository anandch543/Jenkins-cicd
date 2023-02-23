# Tomcat Project 
0. Git clone & 

```
git clone https://github.com/manikcloud/Jenkins-cicd.git
```

00. change the branch

```
git switch  addressbook  
```
1. Install tomcat
 ```
sudo apt update -y
sudo apt install maven tomcat9 tomcat9-admin -y

```
2. change the port number 8080 to 8090

```
sudo vim  /var/lib/tomcat9/conf/server.xml
```
- Find port 8080 and change to 8090
```
 <Connector port="8090" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />


```

- Restart tomcat

``` 
sudo systemctl restart tomcat9

```
- Go to pom location and run the below command

```
 mvn clean install 
```
- copy and paste the war file in tomcat webapp location 
```
sudo cp target/addressbook.war /var/lib/tomcat9/webapps/ -v
```

- url 
```
http://localhost:8090/addressbook/

```


