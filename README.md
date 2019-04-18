
# jenkins-swarm-slave
jenkins-swarm-slave

see: carlossg/jenkins-swarm-slave
see: evarga/jenkins-slave

## Note

This should be done by a cron script on host that fix permission of '/var/run/docker.sock' periodically

```
sudo chmod a+rw /var/run/docker.sock
```

## Auto-provision slaves

- Create a user
e.g. slave/slave_pass

- Replace user/password in deploy descriptor of k8s or docker-compose or export JENKINS_SWARN_SLAVE_COMMAND
e.g. `export JENKINS_SWARN_SLAVE_COMMAND="-username slave -password slave_pass -executors 3"`

## Provision on k8s

- Do steps in 'Auto-provision slaves' section

- Edit jenkins-swarm-slave-secret.yaml

replace `<PUT_JENKINS_SWARN_SLAVE_COMMAND_HERE_MANUALLY>` to `-username slave -password slave_pass -executors 3`

- Run `kubectl create -f jenkins-swarm-slave-secret.yaml` and `kubectl create -f jenkins-swarm-slave-deploy.yaml` to deploy

- `kubectl get po` to see jenkins-swarm-slave's pod

## References

[https://wiki.jenkins-ci.org/display/JENKINS/Swarm+Plugin](https://wiki.jenkins-ci.org/display/JENKINS/Swarm+Plugin)
[https://hub.docker.com/r/csanchez/jenkins-swarm-slave/](https://hub.docker.com/r/csanchez/jenkins-swarm-slave/)
[https://github.com/carlossg/jenkins-swarm-slave-docker](https://github.com/carlossg/jenkins-swarm-slave-docker)

[https://github.com/evarga/docker-images](https://github.com/evarga/docker-images)
[https://github.com/code-troopers/docker-jenkins-slaves](https://github.com/code-troopers/docker-jenkins-slaves)

[https://github.com/yasn77/docker-jenkins-slave](https://github.com/yasn77/docker-jenkins-slave)
[https://github.com/jenkinsci/docker-ssh-slave](https://github.com/jenkinsci/docker-ssh-slave)
