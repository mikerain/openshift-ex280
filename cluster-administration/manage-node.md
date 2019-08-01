---
# Listing pods on nodes

### oc adm manage-node node01 --list-pods
### oc adm manage-node node01 --pod-selector='name=postgresql' --list-pods

# Marking nodes as unschedulable or schedulable

### oc adm manage-node node01 --schedulable=false
### oc adm manage-node node01 --schedulable=true

# Evacuating pods on nodes

### oc adm manage-node  node01 --evacuate --pod-selector='app=app-name'
### oc adm drain node02 --pod-selector='app=app-nameapp=app-name'
