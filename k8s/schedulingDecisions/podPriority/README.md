In this session we will try to learn around Kubernetes scheduling decisions based on pod priority. Pod Priority helps manage and control the order in which pods are scheduled, especially in situations where resources are limited. 

So what you should understand is using pod priority and preemption in Kubernetes is like to building a "fence" around your critical workloads, ensuring they have the resources they need and are scheduled appropriately, especially in resource-constrained environments. This approach helps in managing resource allocation and maintaining service levels for important applications.

Pod priority allows you to specify the importance of different workloads, ensuring that more critical applications are scheduled before less critical ones. This is particularly useful in multi-tenant clusters or when running a mix of high-priority and low-priority applications.

### Key Concepts of Pod Priority

1. **Priority Class**: A resource used to define priority levels. You create priority classes and assign them to pods. Pods with higher priority are scheduled before pods with lower priority when resources are scarce.
    
2. **Preemption**: The process where the scheduler evicts lower priority pods to make room for higher priority pods if the cluster does not have enough resources to schedule the higher priority pods.
    

### Creating Priority Classes

You define priority classes in a Kubernetes cluster by creating `PriorityClass` resources. Each priority class has a `value` that determines its priority level. Higher values indicate higher priority.

#### Example of PriorityClass YAML

```yaml
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: high-priority
value: 1000
globalDefault: false
description: "This priority class is used for high priority pods."

---
apiVersion: scheduling.k8s.io/v1
kind: PriorityClass
metadata:
  name: low-priority
value: 100
globalDefault: false
description: "This priority class is used for low priority pods."

```

These number can go as far as 30million

### Assigning Priority Classes to Pods

You can assign a priority class to a pod by specifying the `priorityClassName` in the pod's manifest.

#### Example of Pod with High Priority

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: high-priority-pod
spec:
  priorityClassName: high-priority
  containers:
  - name: high-priority-container
    image: nginx

```

#### Example of Pod with Low Priority

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: low-priority-pod
spec:
  priorityClassName: low-priority
  containers:
  - name: low-priority-container
    image: nginx

```

### Scheduler Behavior

1. **Scheduling Order**: When there are pending pods and not enough resources, the scheduler will prioritize pods based on their priority class values. Pods with higher priority values are scheduled before those with lower values.
    
2. **Preemption**: If a high-priority pod cannot be scheduled due to resource constraints, the scheduler may preempt (evict) lower priority pods to free up resources. This is controlled by the `preemptionPolicy` field, which defaults to `PreemptLowerPriority` but can be set to `Never` if preemption is not desired.
    

#### Example of Preemption

Consider the following scenario:

- **High-Priority Pod**: `priorityClassName: high-priority`
- **Low-Priority Pod**: `priorityClassName: low-priority`

If a high-priority pod cannot be scheduled due to lack of resources, the scheduler will look for lower priority pods to preempt. If it finds one or more low-priority pods that can be preempted to free up enough resources, it will evict them to schedule the high-priority pod.

### Configuring Preemption Policies

You can control the preemption behavior of individual pods by setting the `preemptionPolicy` field in the pod's spec.

#### Example of Pod with Preemption Policy

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: high-priority-pod
spec:
  priorityClassName: high-priority
  preemptionPolicy: PreemptLowerPriority
  containers:
  - name: high-priority-container
    image: nginx

```

### Handling Pod Priority and Preemption

1. **Avoid Unnecessary Preemption**: Define priority classes carefully to avoid frequent preemption, which can lead to instability.
2. **Balance Resources**: Ensure a balanced resource allocation strategy to minimize the need for preemption.
3. **Use Default Priority**: Optionally, define a default priority class by setting `globalDefault: true` for one of the priority classes, which will be assigned to pods that do not specify a `priorityClassName`.

### Monitoring and Debugging

- **Event Logs**: Monitor event logs to see scheduling and preemption events.
- **Scheduler Logs**: Check scheduler logs for detailed information on scheduling decisions and preemption actions.
- **Metrics**: Use Kubernetes metrics and monitoring tools (like Prometheus) to observe resource usage and scheduling behavior.

### Conclusion

Pod priority in Kubernetes is a powerful feature for managing resource allocation and scheduling in multi-tenant or resource-constrained environments. By defining and assigning priority classes, you can ensure that critical applications receive the resources they need, while less critical applications are scheduled with lower priority. Preemption allows the scheduler to maintain resource availability for high-priority pods, ensuring the cluster remains responsive to important workloads.