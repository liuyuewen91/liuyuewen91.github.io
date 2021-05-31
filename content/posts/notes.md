---
title: "Learning Notes"
date: 2020-08-20T14:38:23+08:00
draft: true
---

## Update statefulset forbidden filed
 
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

## helm 3 release status stuck in `pending-*`

Error message:
```text
$ helm list -a
NAME	NAMESPACE	REVISION	UPDATED                                	STATUS         	CHART     	APP VERSION
test	default  	1       	2021-05-04 20:40:09.827303259 +0000 UTC	pending-install	test-1.1.0	2.0.4
```

Solution:

```shell
helm rollback <release_name> --namespace <name_space> <last_revision_number>
```

example: 
```shell
helm rollback test -n default 1
```
