# Signing Container Images using cosign

## First Login 
./cosign login hub.docker.com -u <username> -p <password>

## sign a container image with a local key pair file
  cosign sign --key cosign.key <IMAGE>


