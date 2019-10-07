---
# Image and Image Stream Management

## Internal Registry Login

docker login docker-registry.default.svc:5000 -u $(oc whoami) -p $(oc whoami -t)   //from any cluster node

oc registry info   //to get registry service name

## Pushing images to internal registry

### Using Docker commands

    docker tag <image-name>:tag <internal-registry>/<project-name>/<image-name>:tag 
    docker push <internal-registry>/<project-name>/<image-name>:tag    // This will result in Image Stream creation 
  
### Using OC commands
oc tag 



