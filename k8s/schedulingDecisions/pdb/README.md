# Scheduling Decisions

| Social Media | Remarks |
| -- | -- |
|Youtube Video | [https://www.youtube.com/watch?v=S94OyTkgXPQ](https://www.youtube.com/watch?v=S94OyTkgXPQ) |
|Twitter/X | [https://twitter.com/itnautomations/status/1784346966446559327](https://x.com/itnautomations/status/1790494300003864707) |

# Summary

Kubernetes, in various scenarios like node recycling, scaling down, or rolling updates,
needs to manage the lifecycle of pods. However, it lacks inherent knowledge of how these
actions may impact the availability of applications running within those pods.

Pod Disruption Budgets (PDBs) serve as a mechanism for users to communicate with Kubernetes
the acceptable level of disruption for their applications. 
By defining a PDB, users specify constraints on the number or percentage of
replicas that must remain available during voluntary disruptions.

When Kubernetes needs to take actions that may disrupt pods,
such as terminating them for maintenance or scaling down,
it consults the PDB associated with those pods. 

The Kubernetes API server uses the information provided by the PDB to ensure that the required
level of availability is maintained.
If the disruption would then violate the constraints specified in the PDB,
Kubernetes will delay or halt the action until it can safely proceed without exceeding the defined disruption budget.
