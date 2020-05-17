# devopstask2
## task description(in steps)
#### 

1.	Create container image that’s has Jenkins installed  using dockerfile 

2.	When we launch this image, it should automatically starts Jenkins service in the container.

 **CODE OF DOCKERFILE**

```
FROM centos
RUN yum install wget -y
RUN wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
RUN rpm --import https://pkg.jenkins.io/redhat/jenkins.io.key
RUN yum install java -y 
RUN yum install jenkins -y
RUN echo -e "jenkins ALL=(ALL) NOPASSWD:ALL">>/etc/sudoers
USER jenkins
ENV USER jenkins
#CMD /etc/rc.d/init.d/jenkins start
 CMD ["java", "-jar", "usr/lib/jenkins/jenkins.war"]
```
To build this image we use following command.

```
docker build -t task:v1/ws1
```
To launch container using this image  we use following command in docker.

``` 
docker run -i -t --name jenkins -p 8080:81 task:v1
```
**Installation of build plugin pipeline**

Jenkins << manage jenkins << manage plugins << available tab << search build pipeline << install build pipeline.

**Create job1**

In this job jenkins automatically pull the code from github repo when developers push the repo in github. 

Jenkins << configure job << name of job(click on freestyle project) << Go to SCM section << click on git << give the repo url << select the dev branch << select build triggers

In the execute shell we use following command

```
sudo cp rvf * /host/task

```




