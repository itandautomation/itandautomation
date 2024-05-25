# ClusterRole

| Social Media | Remarks |
| -- | -- |
|Youtube Video | [https://www.youtube.com/watch?v=p6raRpCWYno]([https://www.youtube.com/watch?v=dTIUw2JHgZE&t=1s](https://www.youtube.com/watch?v=p6raRpCWYno)) |
|Twitter/X | [https://twitter.com/itnautomations/status/1784346966446559327](https://x.com/itnautomations/status/1784679989998223627) |



- cluster-wide resource, it is defined at cluster-scope.

## ClusterRole
```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
	name: my-test-clusterrole
rules:
- apiGroups: [""]
  resources: ["secrets"]
  verbs: ["get", "list", "watch"]

```


## Role

```
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
	namespace: my-own-namespace
	name: my-test-role
rules:
- apiGroups: [""]
  resources: ["pods", "pod/logs"]
  verbs: ["get", "list", "watch"]

```


## Binding

### RoleBinding

```
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
	namespace: my-own-namespace
	name: my-test-rolebinding
subjects:
- kind: User / Group/ Service
  name: itandautomation
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: my-test-role
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: my-test-clusterrole
  apiGroup: rbac.authorization.k8s.io
  
```

### ClusterRoleBinding

```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
	name: my-test-clusterrolebinding
subjects:
- kind: Group
  name: itandautomation-manager
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: my-test-clusterrole
  apiGroup: rbac.authorization.k8s.io
  
```

## Aggregated ClusterRoles

### BaseRole
```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
	name: my-test-baseRole
aggregationRule:
	clusterRoleSelectors:
	- matchLabels:
		my.org.com/aggregate-to-baseRole: "true"
rules: []
```

### Addon-one
```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
	name: addition-to-base-monitoring
	labels:
		my.org.com/aggregate-to-baseRole: "true"
rules:
- apiGroups: [""]
  resources: ["crontabs"]
  verbs: ["get", "list", "watch"]
```

### Addon-two
```
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
	name: addition-to-base
	labels:
		my.org.com/aggregate-to-baseRole: "true"
rules:
- apiGroups: [""]
  resources: ["secrets"]
  verbs: ["get", "list", "watch"]
```
