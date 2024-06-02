# High Availability Stateful Application with Node Affinity and Node Anti-Affinity

```mermaid
graph TD
    subgraph Kubernetes Cluster
        direction LR

        subgraph Node1
            direction TB
            N1Label[disktype=ssd]
            Pod1[Pod1: app=my-app Placed]
        end

        subgraph Node2
            direction TB
            N2Label[disktype=ssd]
            Pod2[Pod2: app=my-app Placed]
        end

        subgraph Node3
            direction TB
            N3Label[disktype=ssd]
            Pod3[Pod3: app=my-app Placed]
        end

        subgraph Node4
            direction TB
            N4Label[disktype=ssd]
            NotPlaced1[Not Placed: app=my-app]
            NotPlaced2[Not Placed: app=my-app]
        end
    end

    N1Label --> Pod1
    N2Label --> Pod2
    N3Label --> Pod3
    N4Label --> NotPlaced1
    N4Label --> NotPlaced2

    Pod1 -- Pod Anti-Affinity --> Pod2
    Pod1 -- Pod Anti-Affinity --> Pod3
    Pod2 -- Pod Anti-Affinity --> Pod3
