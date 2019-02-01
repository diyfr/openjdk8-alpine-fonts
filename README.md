# openjdk8-alpine with fonts

This is a repository for Java Docker base images used in various diyfr (French) projects, requiring fonts

OpenJdk 8 on alpine version, with fonts ttf-dejavu,ttf-ubuntu-font-family, TimeZone update capatibility and custom CA loader.  

Sample Dockerfile for you java app in OpenJDK 8 :  
```
FROM diyfr/openjdk8-alpine-fonts
ENV LANG fr_FR.UTF-8
ENV TZ=Europe/Paris
ADD ./myCA.crt /usr/local/share/ca-certificates/myCA.crt
RUN update-ca-certificates
# Custom volumes
RUN mkdir /logs
RUN mkdir /config
# Define logs directory
VOLUME /logs
# Define application config file directory
VOLUME /config
EXPOSE 8081
COPY target/fr.diyfr.myapp*.jar fr.diyfr.myapp.jar
ENTRYPOINT ["java","-jar","/fr.diyfr.myapp.jar"]
```
