---
# Listing pods on nodes

### oc adm manage-node node01 --list-pods
### oc adm manage-node node01 --pod-selector='name=postgresql' --list-pods

# Marking nodes as unschedulable or schedulable

### oc adm manage-node node01 --schedulable=false
### oc adm manage-node node01 --schedulable=true
