---
title: "Learning Notes"
date: 2020-08-20T14:38:23+08:00
draft: true
---

# Update statefulset forbidden filed
 
Error message:

```
spec: Forbidden: updates to statefulset spec for 
fields other than 'replicas', 'template', and 'updateStrategy' are forbidden"
```

Solution:
1. `kubectl delete statefulset --namespace <name_space> <statefulset_name> --cascade=false`
2. update statefulset
3. delete old pods


`--cascade=true: If true, cascade the deletion of the resources managed by this resource (e.g. Pods created by a
 ReplicationController).  Default true.
`
