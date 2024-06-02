# Kubernetes Pod Placement Flow Chart

Here is an example flow chart illustrating the placement of pods based on node affinity and pod anti-affinity rules.

```mermaid
graph TD
    subgraph Kubernetes Cluster
        direction LR
        
        subgraph Node1
            direction TB
            N1Label[disktype=ssd]
            Pod1[Pod1: app=my-app]
        end

        subgraph Node2
            direction TB
            N2Label[disktype=ssd]
            Pod2[Pod2: app=my-app]
        end

        subgraph Node3
            direction TB
            N3Label[disktype=hdd]
            Pod3[Pod3: cannot place]
        end

        subgraph Node4
            direction TB
            N4Label[disktype=ssd]
            Pod4[Pod4: placeable]
        end

        subgraph Node5
            direction TB
            N5Label[disktype=ssd]
            Pod5[Pod5: cannot place]
        end
    end

    N1Label --> Pod1
    N2Label --> Pod2
    N3Label -.-> Pod3
    N4Label --> Pod4
    N5Label -.-> Pod5

    Pod1 -- Pod Anti-Affinity --> Pod5
    Pod2 -- Pod Anti-Affinity --> Pod5
