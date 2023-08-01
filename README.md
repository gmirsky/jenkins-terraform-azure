# Jenkins Terraform Azure Example

Automating Terraform deployments on Azure using Jenkins

This is a workin progress

docker build -t jenkins-blueocean:2.401.3-1 .

docker run \
  --name jenkins-blueocean \
  --restart=on-failure \
  --detach \
  --network jenkins \
  --env DOCKER_HOST=tcp://docker:2376 \
  --env DOCKER_CERT_PATH=/certs/client \
  --env DOCKER_TLS_VERIFY=1 \
  --publish 8080:8080 \
  --publish 50000:50000 \
  --volume jenkins-data:/var/jenkins_home \
  --volume jenkins-docker-certs:/certs/client:ro \
  jenkins-blueocean:2.401.3-1

docker container exec -it jenkins-blueocean bash

cat /var/jenkins_home/secrets/initialAdminPassword

http://localhost:8080


docker stop jenkins-blueocean