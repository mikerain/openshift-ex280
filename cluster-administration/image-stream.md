### Create New image stream
oc import-image <is-name> --from='external registry name'

oc import-image my-buyxbox --from='rajeshd2090/busy:v1'

### Add new tag to image stream
oc tag <source-repo-with-tag> <image-stream-with-tag> --source=docker
  
oc tag rajeshd2090/busybox:g1 busy:v2 --source=docker

### Delete tag from image stream


### Modify tag of image stream
