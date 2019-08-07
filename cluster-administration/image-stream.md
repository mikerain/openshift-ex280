## oc image-stream
### Create New image stream
oc import-image <is-name> --from='external registry name'

oc import-image my-buyxbox --from='rajeshd2090/busy:v1'

## oc tag
### Add new tag to image stream
oc tag <source-repo-with-tag> <image-stream-with-tag> --source=docker
  
oc tag rajeshd2090/busybox:g1 busy:v2 --source=docker

### Delete tag from image stream
oc tag <image-stream-name-with-tag> --delete

oc tag busy:v3 --delete

### Modify tag of image stream
oc tag <source-repo-with-tag> <image-stream-with-tag> --source=docker

oc tag rajeshd2090/busybox:g2 busy:v1 --source=docker

## oc image

### Image mirror from one repo to other

oc image mirror rajeshd2090/busy:v1 rajeshd2090/busybox:v10


### describe image stream

oc describe is <image-stream-name>
  
### list image stream from project

oc get is
