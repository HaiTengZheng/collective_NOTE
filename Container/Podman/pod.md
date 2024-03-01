# pod
Concept: a group of one or more containers working together for a common purpose 
         and sharing the same `namespaces` and `cgroups` (resource constraints)
- on SELinux machines, all container process within a pod share the same SELinux 
  labels
- support `infra container` (pause container)
- support more than one `sidcar container`
- the containers within the pod share the same network namespaces, port binding
    is shared by all of the containers.
- the containers in pods shared the same SELinux label, which means they can
    share the same volumes.

## support two kinds of init container
- Once - only run the first time the pod is created
- Always - runs every time the pod is created

## create a pod
> podman pod create
## adding a container to a pod
with `--pod pod_name` option
> podamn create --pod mypod ...


# infra container (pause container)
pod always include the infra container, each pod will have a different 
infra container
- the infra container only holds open the namespaces and cgroups from the
  kernel, allowing containers to come and go within the pod
- the infra container is based on the k8s.gcr.io/pause image    
- the infra container has a monitor process: `common`, monitoring it.

# conmon
a lightweight C program monitor the container until it exits
- the infra has a container monitor process
- every container within a pod has its own conmon

# sidcar container
sidcar container often monitor the primary container
