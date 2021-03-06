---
# Image and Image Stream Management

## Internal Registry Login

    docker login docker-registry.default.svc:5000 -u $(oc whoami) -p $(oc whoami -t)   //from any cluster node

    oc registry info   //to get registry service name

## RBAC for image-streams and Openshift registry

### image-puller role: Access image-stream from other project

    service account of target project should have permission to access image-stream from source project(IS-Project)
    $ oc adm policy add-role-to-user system:image-puller system:serviceaccounts:<target-project-name> -n=<IS-Project>
    
### registry-admin role: Admin access to registry. Can provide registry access roles to other users

    $ oc adm policy add-cluster-role-to-user registry-admin <user-name>
    
### registry-editor role: Editor access to registry. Same as admin minus registry access roles to other users

    $ oc adm policy add-cluster-role-to-user registry-editor <user-name>
    
### registry-viewer role: View access to registry. 
   
    $ oc adm policy add-cluster-role-to-user registry-viewer <user-name> 
    $ oc adm policy add-role-to-user registry-viewer <user-name> -n <project-name>
    

## Pushing images to internal registry

### Using Docker commands

    $ docker tag <image-name>:tag <internal-registry>/<project-name>/<image-name>:tag 
    $ docker push <internal-registry>/<project-name>/<image-name>:tag    // This will result in Image Stream creation 
  
### Loading from tar ball

    $ docker image load -i <file-name>.tar       // docker image save -o <file-name>.tar to convert image to tar file
    $ docker tag <image-name>:tag <internal-registry>/<project-name>/<image-name>:tag 
    $ docker push <internal-registry>/<project-name>/<image-name>:tag    // This will result in Image Stream creation 
    
    
### Using OC commands

    $ oc tag <image-stream> <image-stream>
    $ oc tag --source=docker <docker-image> <image-stream>
    
## Removing images from internal registry    

### Remove image-stream tag

    $ oc tag <image-stream>:tag -d
    
### Remove image-stream

    $ oc delete imagestream ruby
    
## oc image-stream
### Create New image stream
   
    $ oc import-image <is-name> --from='external registry name'
    $ oc import-image my-buyxbox --from='rajeshd2090/busy:v1'

## oc tag
### Add new tag to image stream

    $ oc tag <source-repo-with-tag> <image-stream-with-tag> --source=docker
    $ oc tag rajeshd2090/busybox:g1 busy:v2 --source=docker

### Delete tag from image stream

    $ oc tag <image-stream-name-with-tag> --delete
    $ oc tag busy:v3 --delete

### Modify tag of image stream

    $ oc tag <source-repo-with-tag> <image-stream-with-tag> --source=docker
    $ oc tag rajeshd2090/busybox:g2 busy:v1 --source=docker

## oc image

### Image mirror from one repo to other

    $ oc image mirror rajeshd2090/busy:v1 rajeshd2090/busybox:v10

### describe image stream

    $ oc describe is <image-stream-name>
  
### list image stream from project

    $ oc get is


    
    



