# Write a dockerfile for installing openjdk15 and build the image

### Approach 1
Downloading the openjdk 15 tar file from official website, untar the file and set the path to java binary.

##### Create a Dockerfile and copy a  below content

```Dockerfile
FROM centos:8

ENV PATH=$PATH:/opt/java/jdk-15.0.2/bin

RUN yum install tar gzip

WORKDIR /opt/java

RUN curl https://download.java.net/java/GA/jdk15.0.2/0d1cfde4252546c6931946de8db48ee2/7/GPL/openjdk-15.0.2_linux-x64_bin.tar.gz -o openjdk-15.0.2_linux-x64_bin.tar.gz

RUN tar -xzf openjdk-15.0.2_linux-x64_bin.tar.gz && \
    rm -rf openjdk-15.0.2_linux-x64_bin.tar.gz
```
##### Build a docker image
```
docker build -t java:15 .
```
##### Check the size of docker image
Run the following command to check the docker images avilable in local machine
```
docker images
```
![Docker Images](https://github.com/vigneshsweekaran/vigneshsweekaran.github.io/blob/master/docker/tutorials/images/openjdk-15-docker-images.png)

##### Create a docker container from the created image and check the java version
```Docker
docker run --rm java:15 java -version
```
![checking java version]()