
# Running Jenkins Server Docker image locally
docker run --name myjenkins-blueocean --restart=on-failure --detach --network jenkins --env DOCKER_HOST=tcp://docker:2376 --env DOCKER_CERT_PATH=/certs/client --env DOCKER_TLS_VERIFY=1 --publish 8080:8080 --publish 50000:50000 --volume jenkins-data:/var/jenkins_home --volume jenkins-docker-certs:/certs/client:ro yogendra123raju/jenkins 
## Signing process 
docker ps -a
docker exec -it  <containerID> sh
# Login to Docker
docker login -u <Username> -p <password>
# View Logs of running container
docker logs <containerID>

