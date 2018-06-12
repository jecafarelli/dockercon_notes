## Java

Make the images small by using multi stag build

Install dependencies like line below:
```
ADD pom.xml .
RUN mvn -B -f pom.xml -s /usr/share/maven/ref/settings-docker.xml dependency:resolve
```
