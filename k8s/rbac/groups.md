# Groups

| Social Media | Remarks |
| -- | -- |
|Youtube Video | [https://www.youtube.com/watch?v=p18Tr39FkfA](https://www.youtube.com/watch?v=p18Tr39FkfA) |
|Twitter/X | [https://x.com/itnautomations/status/1784679233505185947](https://x.com/itnautomations/status/1784679233505185947) |

## Summary

In Kubernetes, a group is not a direct resource like a Pod or a Service.

Instead, it's a concept used for authentication and authorization purposes.
Groups are collections of users or other groups and are used to manage access control to Kubernetes resources.

When you create a ClusterRole and attach it to a ClusterRoleBinding,
you can specify subjects, such as users, service accounts, or groups,
that should have the permissions defined by the ClusterRole.

If you specify a group as a subject, Kubernetes will check whether any users or service accounts belong to that group and grant them the permissions accordingly.

If the group specified in the ClusterRoleBinding does not exist, Kubernetes will create a new group.

In summary, when attaching a ClusterRole to a ClusterRoleBinding with a group as a subject:

- If the group already exists and contains users or service accounts, those users or service accounts will be granted the permissions defined by the ClusterRole.
- If the group does not exist it will create a new group and grant permissions.

## Risk factor

Groups & Groups of Groups should be dealt with care as it can lead to potential permission escalation.
