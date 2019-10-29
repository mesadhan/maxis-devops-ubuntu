# Maxis DevOps Pipeline Configuration


## Up and runing guideline to start pipeline

- `vagrant ssh` into machine
- cd to `home/vagrant/vagrant-data/devops-pipeline`
- then `docker-compose up -d` Or
- If container `already started before` then just use `docker ps` to show that container Id. then start it
using `docker start <containerId>`

> Services:

- http://localhost:7001
- http://localhost:13000

## Jenkins CI/CD Server Setup

1. Make Sure MaxisHub server up and running properly,
2. Create Credential for `MaxisHub` and `DockerHub`
3. To `Maven` & `Docker` Tools setup follow below steps,


- `Home` -> `Manage Jenkins` -> `Global Tool Configuration`
- `Maven` section add [ Name: `myMaven`, version: `3.5.2` ]
- `Docker` section add [ Name: `myDocker`, Checked: `Install automatically`, Download from: docker.com: `latest` ]


4. Create new job using `Multibrach Pipeline`, following

    1.From `General` -> `Branch Sources`

    - Project Repository: `git project url`
    - Credentials: `put previous configed credential`

    2.Build Configuration

    - Mode: `by Jenkinsfile`
    - Script Path: `Jenkinsfile`


Apply, Save Then

5. Build Now





# References

 - http://localhost:7001/administrativeMonitor/OldData/manage
 - https://engineering.taboola.com/5-simple-tips-boosting-jenkins-performance/
 - https://engineering.taboola.com/scaling-out-jenkins-based-ci-with-docker-and-nomad/