# Understanding & Removing Terminating Namespace in Kubernetes

| Social Media | Remarks |
| -- | -- |
|Youtube Video | https://www.youtube.com/watch?v=0c3YPCa_16Y |
|Twitter/X | https://twitter.com/itnautomations/status/1784346966446559327 |

## Summary

### Commands

1. `kubectl delete ns example-namespace --force --grace-period=0`
2. `export NAMESPACE=example-namespace; kubectl get ns ${NAMESPACE} -o json | jq '.spec.finalizers = []' | kubectl replace --raw "/api/v1/namespaces/${NAMESPACE}/finalize" -f -`
