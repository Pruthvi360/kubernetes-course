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

## ALL OTHER INFREQUENT COMMANDS

| Command | Syntax | Description |
|---------|--------|-------------|
| api-resources | `kubectl api-resources [OPTIONS]` | Print the supported API resources on the server. |
| api-versions | `kubectl api-versions [OPTIONS]` | Print the supported API versions on the server, in the form of "group/version". |
| auth can-i | `kubectl auth can-i [OPTIONS] VERB [TYPE | TYPE/NAME | TYPE/NAME/RESOURCE]` | Check if the current user can perform an action on a resource. |
| auth reconcile | `kubectl auth reconcile [OPTIONS]` | Reconcile the authorization policy for a user. |
| certificate approve | `kubectl certificate approve [OPTIONS] NAME` | Approve a certificate signing request (CSR). |
| certificate deny | `kubectl certificate deny [OPTIONS] NAME` | Deny a certificate signing request (CSR). |
| certificate renew | `kubectl certificate renew [OPTIONS] NAME` | Renew a certificate signing request (CSR). |
| cluster-info dump | `kubectl cluster-info dump [OPTIONS]` | Dump cluster info to stdout. |
| completion bash | `kubectl completion bash [OPTIONS]` | Output shell completion for bash. |
| completion zsh | `kubectl completion zsh [OPTIONS]` | Output shell completion for zsh. |
| convert | `kubectl convert [OPTIONS] FILE` | Convert config files between different API versions. |
| debug | `kubectl debug [OPTIONS] POD [-c CONTAINER]` | Create a debugging session for a running container in a pod. |
| describe csr | `kubectl describe csr [NAME]` | Show details about a certificate signing request (CSR). |
| drain | `kubectl drain [OPTIONS] NODE` | Drain a node in preparation for maintenance. |
| explain | `kubectl explain [OPTIONS] [KIND]` | Documentation of resources. |
| get all | `kubectl get all [OPTIONS] [NAME  -l LABEL]` | Display all resources in the cluster. |
| get certificatesigningrequests | `kubectl get certificatesigningrequests [OPTIONS] [NAME  -l LABEL]` | List certificate signing requests (CSRs). |
| get componentstatuses | `kubectl get componentstatuses [OPTIONS] [NAME  -l LABEL]` | List the condition of different components running on the cluster. |
| get configmap | `kubectl get configmap [OPTIONS] [NAME  -l LABEL]` | Show information about a specific config map or a list of config maps. |
| get csr | `kubectl get csr [OPTIONS] [NAME  -l LABEL]` | List certificate signing requests (CSRs). |
| get daemonset | `kubectl get daemonset [OPTIONS] [NAME  -l LABEL]` | List daemon sets. |
| get deployment | `kubectl get deployment [OPTIONS] [NAME  -l LABEL]` | List deployments. |
| get events | `kubectl get events [OPTIONS] [NAME  -l LABEL]` | List events. |
| get ingress | `kubectl get ingress [OPTIONS] [NAME  -l LABEL]` | List ingress. |
| get job | `kubectl get job [OPTIONS] [NAME  -l LABEL]` | List jobs. |
| get namespace | `kubectl get namespace [OPTIONS] [NAME  -l LABEL]` | List namespaces. |
| get node | `kubectl get node [OPTIONS] [NAME  -l LABEL]` | List nodes. |
| get persistentvolume | `kubectl get persistentvolume [OPTIONS] [NAME  -l LABEL]` | List persistent volumes. |
| get pod | `kubectl get pod [OPTIONS] [NAME  -l LABEL]` | List pods. |
| get replicaset | `kubectl get replicaset [OPTIONS] [NAME  -l LABEL]` | List replica sets. |
| get secret | `kubectl get secret [OPTIONS] [NAME  -l LABEL]` | List secrets. |
| get service | `kubectl get service [OPTIONS] [NAME  -l LABEL]` | List services. |
| get statefulset | `kubectl get statefulset [OPTIONS] [NAME  -l LABEL]` | List stateful sets. |
| get storageclass | `kubectl get storageclass [OPTIONS] [NAME  -l LABEL]` | List storage classes. |
| get user | `kubectl get user [OPTIONS] [NAME  -l LABEL]` | List users. |
| get volumeattachment | `kubectl get volumeattachment [OPTIONS] [NAME  -l LABEL]` | List volume attachments. |
| label | `kubectl label [OPTIONS] RESOURCE NAME KEY=VALUE` | Add or update labels on a resource. |
| logs | `kubectl logs [OPTIONS] POD [-c CONTAINER]` | Print the logs for a container in a pod. |
| rollout history | `kubectl rollout history [OPTIONS] RESOURCE NAME` | View rollout history of a resource. |
| rollout pause | `kubectl rollout pause [OPTIONS] RESOURCE NAME` | Pause the rollout of a resource. |
| rollout resume | `kubectl rollout resume [OPTIONS] RESOURCE NAME` | Resume the rollout of a paused resource. |
| rollout status | `kubectl rollout status [OPTIONS] RESOURCE NAME` | Show the status of a rollout. |
| rollout undo | `kubectl rollout undo [OPTIONS] RESOURCE NAME` | Undo a previous rollout of a resource. |
| rollout restart | `kubectl rollout restart [OPTIONS] RESOURCE NAME` | Restart a rollout of a resource. |

