# Kubernetes

## Components
- API Server: acts as the frontend for k8s. The users, management devices, command-line interfaces, all talk to the API server to interact with the k8s cluster.
  
- etcd: is a distributed, reliable key value store used by k8s to store all data used to manage the cluster. Think of it this way, when you have multiple nodes and multiple master in you cluster, etcd stores all that information on all the nodes in the cluster in a distributed manner. ETCD is responsbible for implements locks within the cluster to ensure that there are no conflics between the master

- kubelet: is the agent that runs on each node in the cluster. It is responsible for ensuring that containers are running in a pod. The kubelet takes a set of PodSpecs and ensures that the containers described in those PodSpecs are running and healthy. It communicates with the API server to get the desired state of the pods and reports back the current state.

- Container Runtime: is the underlying software that is used to run containers. It can be Docker, containerd, CRI-O, etc. The container runtime is responsible for pulling images from a registry, starting and stopping containers, and managing the lifecycle of containers.

- Controller: are the brain behind orchestration. They're responsible for noticing and responding when nodes, containers or endpoints goes down. The controllers make decisions to bring up new containers, delete containers, or reschedule containers to other nodes. They are responsible for maintaining the desired state of the cluster. 

- Scheduler: is responsible for distribuiting work or containers accross multiple nodes. It looks for newly created containers and assigns them to nodes

## 2 types of servers
- master node: responsible for managing the cluster. It runs the API server, etcd, kube-controller-manager, kube-scheduler, and other control plane components. The master node is responsible for maintaining the desired state of the cluster and making decisions about scheduling and scaling.
- 
- worker node: is where the actual work is done. It runs the kubelet, container runtime, and pods. The worker node is responsible for running the containers and reporting back to the master node about the state of the pods.

## kubectl
`kubectl` is the command-line tool used to interact with the Kubernetes API server. It allows you to create, update, delete, and get information about resources in the cluster.

# Core concepts
- Pod: is the smallest and simplest Kubernetes object. It represents a single instance of a running process in your cluster. Pods can contain one or more containers, and they share the same network namespace

```yaml
# creates a new pod from a YAML file pod-definition.yml
kubectl create -f pod-definition.yml

# creates a new pod named "nginx" with the nginx image and exposes port 80.
kubectl run nginx --image=nginx --port=80

# get the list of pods in the current namespace
kubeclt get pods

# get the details of the nginx pod
kubectl describe pod myapp-pod
```

- Service: is an abstraction that defines a logical set of pods and a policy by which to access them. Services enable communication between different parts of your application and provide a stable endpoint for accessing pods
- 
- Deployment: is a higher-level abstraction that manages a set of replicas of a pod.



| Kind       | Version |
| ---------- | ------- |
| Pod        | v1      |
| Service    | v1      |
| ReplicaSet | apps/v1 |
| Deployment | apps/v1 |

