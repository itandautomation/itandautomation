# POD topology spread constraints

| Social Media  | Remarks                                                                                    |
| ------------- | ------------------------------------------------------------------------------------------ |
| Youtube Video | [https://www.youtube.com/watch?v=t9bAMhbVpAM](https://www.youtube.com/watch?v=bGP8yu--3eM) |
| Twitter/X     | [https://x.com/itnautomations](https://x.com/itnautomations)                               |


Topology Spread Constraints in Kubernetes are a feature that allows you to control the distribution of pods across different topology domains (such as nodes, zones, or regions), that is in order to  ensure balanced scheduling and high availability. This feature is particularly useful in multi-zone or multi-region clusters, where you want to avoid overloading any single domain and enhance fault tolerance. However, it is also important on multi-AZ clusters which is very common, and you can picture same concept within AZ layer.

If you are running nodes in 3 availability zone and create proportion of node in each, you want to spread your pods into all of those different AZ. Bin packing should be avoided. Exactly when you would want to use Topology Spread Constraints.

Which ever layer of fault you want to tolerate; regional or multi-zone you would want to use Topology spread constraints.

### Key Concepts of Topology Spread Constraints

1. **TopologyKey**: This specifies the key used to denote the topology domain. Common examples can be:
    - `topology.kubernetes.io/zone`: Represents zones within a region.
    - `topology.kubernetes.io/region`: Represents geographic regions.
    - failure-domain.beta.kubernetes.io/zone 
    - failure-domain.beta.kubernetes.io/region
1. **MaxSkew**: This defines the maximum allowable difference in the number of pods between the most and least loaded topology domain. A lower `maxSkew` value ensures tighter distribution but may result in more scheduling constraints.
    
3. **WhenUnsatisfiable**: This parameter defines the action to take when the constraint cannot be met. Possible values are:
    
    - `DoNotSchedule`: The scheduler will not schedule the pod if the constraint is violated.
    - `ScheduleAnyway`: The scheduler will place the pod even if it results in a skew that violates the constraint.
4. **LabelSelector**: This is used to identify the set of pods to which the constraint applies. Pods that match this selector are considered for distribution.
    

### Example of Topology Spread Constraints

Here is a detailed example of how to use Topology Spread Constraints in a Kubernetes Deployment YAML:


```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-app
spec:
  replicas: 6
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      topologySpreadConstraints:
      - maxSkew: 1
        topologyKey: "topology.kubernetes.io/zone"
        whenUnsatisfiable: DoNotSchedule
        labelSelector:
          matchLabels:
            app: web
      containers:
      - name: web
        image: nginx

```

In this example:

- **TopologyKey**: `topology.kubernetes.io/zone` ensures that the pods are spread across different zones.
- **MaxSkew**: `1` means that the difference in the number of pods between the zones should not be more than 1.
- **WhenUnsatisfiable**: `DoNotSchedule` tells the scheduler not to schedule the pod if it would violate the skew constraint.
- **LabelSelector**: `app: web` selects pods with the label `app: web` to apply the constraint.


Lets talk about maxskew





### How It Works

1. **Pod Distribution**: The scheduler attempts to distribute the specified number of replicas across the available zones (or other topology domains) as evenly as possible. If there are three zones, for instance, the scheduler will try to place 2 pods in each zone if there are 6 replicas.
2. **MaxSkew Enforcement**: The `maxSkew` value ensures that the distribution remains balanced. If one zone already has 2 pods and another has 1 pod, the scheduler will not place a third pod in the first zone unless the second zone gets its second pod.
3. **Handling Violations**: If the `whenUnsatisfiable` policy is `DoNotSchedule`, the scheduler will hold off scheduling a pod that would violate the constraint, potentially leading to pending pods. If set to `ScheduleAnyway`, the scheduler will place the pod even if it exceeds the skew, ensuring that the pod is scheduled but potentially resulting in imbalance.

### Benefits of Using Topology Spread Constraints

- **High Availability**: By spreading pods across multiple topology domains, applications can remain available even if a single domain fails.
- **Load Balancing**: Distributing pods evenly across nodes, zones, or regions can help in balancing the load and avoiding hotspots.
- **Resource Utilization**: Efficient spreading of pods ensures better utilization of cluster resources, preventing some nodes or zones from being overloaded while others are underutilized.

### Use Cases

1. **Multi-Zone or Multi-Region Deployments**: Ensuring that an application remains available and performant across different geographical locations.
2. **Critical Workloads**: Distributing replicas of critical applications to avoid single points of failure.
3. **Load Balancing**: Enhancing the overall performance and reliability of the system by balancing the workload.

### Limitations and Considerations

- **Complexity**: Configuring topology spread constraints can add complexity to the deployment configuration.
- **Pending Pods**: If constraints are too strict (e.g., low `maxSkew`), it might result in pods not being scheduled, leading to application availability issues.
- **Cluster State Awareness**: The scheduler’s decisions are based on the current state of the cluster, which can change, leading to potential rebalancing needs.

In summary, Topology Spread Constraints in Kubernetes provide a powerful mechanism to control the distribution of pods across different topology domains, enhancing fault tolerance, availability, and resource utilization in your cluster. Properly configuring these constraints can help achieve a well-balanced and resilient deployment architecture.
