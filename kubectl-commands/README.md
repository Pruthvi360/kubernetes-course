# List of command and explaination
## `kubectl` Commands

Below is a list of commonly used `kubectl` commands along with their syntax and brief explanations:

| Command | Syntax | Description |
|---------|--------|-------------|
| apply | `kubectl apply [OPTIONS] -f FILE` | Create or update resources in a cluster from a configuration file. |
| attach | `kubectl attach [OPTIONS] POD -c CONTAINER` | Attach to a running container. |
| auth | `kubectl auth [OPTIONS] SUBCOMMAND` | Inspect authorization options. |
| autoscale | `kubectl autoscale [OPTIONS] RESOURCE NAME --min=MIN --max=MAX` | Automatically scale a resource based on CPU utilization or custom metrics. |
| certificate | `kubectl certificate [OPTIONS] SUBCOMMAND` | Modify certificate resources. |
| cluster-info | `kubectl cluster-info [OPTIONS]` | Display information about the cluster. |
| completion | `kubectl completion [OPTIONS] [COMMAND]` | Output shell completion code for `kubectl`. |
| config | `kubectl config [OPTIONS] SUBCOMMAND` | Modify kubeconfig files. |
| cordon | `kubectl cordon [OPTIONS] NODE` | Mark a node as unschedulable. |
| cp | `kubectl cp [OPTIONS] SOURCE DESTINATION` | Copy files and directories to and from containers. |
| create | `kubectl create [OPTIONS] -f FILE` | Create a resource from a file or by specifying its attributes. |
| delete | `kubectl delete [OPTIONS] RESOURCE NAME` | Delete resources by name or based on a configuration file. |
| describe | `kubectl describe [OPTIONS] RESOURCE NAME` | Show detailed information about a specific resource or set of resources. |
| diff | `kubectl diff [OPTIONS] -f FILE` | Diff live configuration against a file or stdin. |
| drain | `kubectl drain [OPTIONS] NODE` | Drain a node in preparation for maintenance. |
| edit | `kubectl edit [OPTIONS] RESOURCE NAME` | Edit a resource on the fly using the default editor. |
| exec | `kubectl exec [OPTIONS] POD COMMAND [CONTAINER]` | Execute a command in a container. |
| explain | `kubectl explain [OPTIONS] [KIND]` | Documentation of resources. |
| expose | `kubectl expose [OPTIONS] RESOURCE NAME --port=PORT [--target-port=TARGET-PORT]` | Expose a deployment, pod, or service as a new Kubernetes service. |
| get | `kubectl get [OPTIONS] RESOURCE [NAME]` | Retrieve information about resources. |
| kustomize | `kubectl kustomize [OPTIONS] [DIR | FILE]` | Build a Kubernetes API object from a Kustomization file. |
| label | `kubectl label [OPTIONS] RESOURCE NAME KEY=VALUE` | Add or update labels on a resource. |
| logs | `kubectl logs [OPTIONS] POD [-c CONTAINER]` | Print the logs for a container in a pod. |
| patch | `kubectl patch [OPTIONS] RESOURCE NAME -p PATCH` | Update field(s) of a resource. |
| plugin | `kubectl plugin [OPTIONS] [COMMAND]` | Provides utilities for interacting with plugins. |
| port-forward | `kubectl port-forward [OPTIONS] POD [LOCAL_PORT:]REMOTE_PORT` | Forward one or more local ports to a pod. |
| proxy | `kubectl proxy [OPTIONS]` | Run a proxy to the Kubernetes API server. |
| replace | `kubectl replace [OPTIONS] -f FILE` | Replace a resource by filename or stdin. |
| rollout | `kubectl rollout [OPTIONS] SUBCOMMAND [args]` | Manage the rollout of a resource. |
| run | `kubectl run [OPTIONS] --image=IMAGE -- [COMMAND] [ARG...]` | Run a particular image on the cluster. |
| scale | `kubectl scale [OPTIONS] RESOURCE NAME --replicas=COUNT` | Change the number of replicas for a deployment, replication controller, or replica set. |
| set | `kubectl set [OPTIONS] SUBCOMMAND [args]` | Set specific features on objects. |
| taint | `kubectl taint [OPTIONS] NODE KEY=VALUE:TOLERATION` | Update the taints on one or more nodes. |
| top | `kubectl top [OPTIONS] [POD | TYPE/NAME] [CONTAINER]` | Display resource usage. |
| uncordon | `kubectl uncordon [OPTIONS] NODE` | Mark a node as schedulable. |
| version | `kubectl version [OPTIONS]` | Print the client and server versions. |
