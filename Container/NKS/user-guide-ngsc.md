## Container > NHN Kubernetes Service (NKS) > User Guide

## Cluster
Cluster refers to a group of instances that comprise user's Kubernetes.

### Creating Clusters
To use NHN Kubernetes Service (NKS), you must first create a cluster. Go to **Container > NHN Kubernetes Service (NKS)** and click **Create Cluster**, and a page for creating clusters shows up. The following items are required to create a cluster:

| Item | Description |
| --- | --- |
| Cluster Name | Name of a Kubernetes cluster. It is limited to 20 characters, and only lowercase English letters, numbers, and '-' can be entered. It must start with a lowercase letter and end with a lowercase letter or number. |
| Kubernetes Version | Kubernetes version to use |
| VPC | VPC network to be attached to clusters |
| Subnet | Subnet to be associated with instances that comprise a cluster, among those defined in VPC |
| Image | Images for instances comprising a cluster |
| Availability Zone | Area to create a default node group instance |
| Flavor | Instance specifications for a default node group |
| Node Count | Number of instances for a default node group |
| Key Pair | Key pair to access default node group |
| Block Storage Type | Type of block storage for a default node group instance |
| Block Storage Size | Size of block storage for a default node group instance |

NHN Kubernetes Service (NKS) supports several versions of Kubernetes. Some features may be restricted depending on the version.

| Version | Creating a new cluster | Using the created cluster|
| :-: | :-: | :-: |
| v1.17.6 | Unavailable | Available |
| v1.18.19 | Unavailable | Available |
| v1.19.13 | Unavailable | Available |
| v1.20.12 | Available | Available |
| v1.21.6 | Available | Available |
| v1.22.3 | Available | Available |
| v1.23.3 | Available | Available |


Enter information as required and click **Create Cluster**, and a cluster begins to be created. You can check the status from the list of clusters. It takes about 10 minutes to create; more time may be required depending on the cluster configuration.


### Querying Clusters
A newly created cluster can be found in the **Container > NHN Kubernetes Service (NKS)** page. Select a cluster and the information is displayed at the bottom.

| Item | Description |
| --- | --- |
| Cluster Name | Name and ID of Kubernetes Cluster |
| Node Count | Number of instances of all nodes comprising a cluster |
| Kubernetes Version | Kubernetes version in service |
| VPC | VPC network attached to cluster |
| Subnet | Subnet associated to a node instance comprising a cluster |
| API Endpoint | URI of API endpoint to access cluster for operation |
| Configuration File | Download button of configuration file required to access cluster for operation |

### Deleting Clusters
Select a cluster to delete, and click **Delete Clusters** and it is deleted. It takes about 5 minutes to delete; more time may be required depending on the cluster status.

## Node Group
A node group is comprised of worker node instances that comprise a Kubernetes.

### Querying Node Groups
Click a cluster name on the list to find the list of node groups. Select a node group and the information shows at the bottom.

* Basic Information
On the **Basic Information** tab, you can check the following:

| Item | Description |
| --- | --- |
| Node Group Name | Name and ID of a node group |
| Cluster Name | Name and ID of a cluster to which a node group is included |
| Kubernetes Version | Kubernetes version in service |
| Availability Zone | Area in which a node group instance is created |
| Flavor | Specifications of a node group instance |
| Image Type | Type of image for a node group instance |
| Block Storage Size | Size of block storage for a node group instance |
| Created Date | Time when node group was created |
| Modified Date | Last time when node group was modified |

* List of Nodes
Find the list of instances comprising a node group from the **List of Nodes** tab.

### Creating Node Groups
Along with a new cluster, a default node group is created, but more node groups can be created depending on the needs. If higher specifications are required to run a container, or more worker node instances are required to scale out, node groups may be additionally created. Click **Create Node Groups** from the page of node group list, and the page of creating a node group shows up. The following items are required to create a node group:

| Item | Description |
| --- | --- |
| Availability Zone | Area to create instances comprising a cluster |
| Node Group Name | Name of an additional node group. It is limited to 20 characters, and only lowercase English letters, numbers, and '-' can be entered. It must start with a lowercase letter and end with a lowercase letter or number. |
| Flavor | Specifications of an instance for additional node group |
| Node Count | Number of instances for additional node group |
| Key Pair | Key pair to access additional node group |
| Block Storage Type | Type of block storage of instance for additional node group |
| Block Storage Size | Size of block storage of instance for additional node group |

Enter information as required and click **Create Node Groups**, and a node group begins to be created. You may check status from the list of node groups. It takes about 5 minutes to create; more time may be required depending on the node group setting.

>[Caution]
>Only the user who created the cluster can create node groups.

### Deleting Node Groups
Select a node group to delete from the list of node groups, and click **Delete Node Groups** and it is deleted. It takes about 5 minutes to delete a node group; more time may be required depending on the node group status.

### Adding node to node group
Nodes can be added to operating node groups. The current list of nodes will appear upon clicking the node list tab on the node group information query page. Nodes can be added by selecting the Add Node button and entering the number of nodes you want.

>[Caution]
>Nodes cannot be manually added to node groups on which autoscaler is enabled.

### Deleting node from node group
Nodes can be deleted from operating node groups. The current list of nodes will appear upon clicking the node list tab on the node group information query page. A confirmation dialog box will appear when a user selects nodes for deletion and clicks the Delete Node button. When the user confirms the node name and selects the OK button, the node will be deleted.

>[Caution]
>Pods that were operating in the deleted node will go through force shutdown. To safely transfer pods from the currently operating nodes to be deleted to other nodes, you must run the "drain" command. New pods can be scheduled on nodes even after they are drained. To prevent new pods from being scheduled in nodes that are to be deleted, you must run the "cordon" command. For more information on safe node management, see the document below.

>[Caution]
>Nodes cannot be manually deleted from node groups on which autoscaler is enabled.

* [Safe node drain](https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/)
* [Manual node management](https://kubernetes.io/docs/concepts/architecture/nodes/#manual-node-administration)

### Using a GPU node group 
When you need to run GPU-based workloads through Kubernetes, you can create a node group composed of GPU instances.
Select the `g2` type when selecting a flavor while creating the clusters or node groups to create a GPU node group.

> [Note]
> GPU provided by NHN Cloud GPU instance is affiliated with NVIDIA. ([Identify available GPU specifications that can be used](/Compute/GPU%20Instance/zh/overview/#gpu-specifications))
> nvidia-device-plugin required for Kubernetes to use an NVIDIA GPU will be installed automatically when creating a GPU node group.

To check the default setting and run a simple operation test for the created GPU node, use the following method:

#### Node level status check
Access the GPU node and run the `nvidia-smi` command.
The GPU driver is working normally if the output shows the following:

```
$ nvidia-smi
Mon Jul 27 14:38:07 2020
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 418.152.00   Driver Version: 418.152.00   CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Tesla T4            Off  | 00000000:00:05.0 Off |                    0 |
| N/A   30C    P8     9W /  70W |      0MiB / 15079MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+ 
```

#### Kubernetes level status check
Use the `kubectl` command to view information about available GPU resources at the cluster level.
Below are commands and execution results that displays the number of GPU cores available for each node.

```
$ kubectl get nodes -A -o custom-columns='NAME:.metadata.name,GPU Allocatable:.status.allocatable.nvidia\.com/gpu,GPU Capacity:.status.capacity.nvidia\.com/gpu'
NAME                                       GPU Allocatable   GPU Capacity
my-cluster-default-w-vdqxpwisjjsk-node-1   1                 1
```

#### Sample workload execution for GPU testing
GPU nodes that belong to Kubernetes clusters provide resources such as `nvidia.com/gpu` in addition to CPU and memory.
To use GPU, enter as shown in the sample file below to be allocated with the `nvidia.com/gpu` resource.

* resnet.yaml
```
apiVersion: v1
kind: Pod
metadata:
  name: resnet-gpu-pod
spec:
  imagePullSecrets:
    - name: nvcr.dgxkey
  containers:
    - name: resnet
      image: nvcr.io/nvidia/tensorflow:18.07-py3
      command: ["mpiexec"]
      args: ["--allow-run-as-root", "--bind-to", "socket", "-np", "1", "python", "/opt/tensorflow/nvidia-examples/cnn/resnet.py", "--layers=50", "--precision=fp16", "--batch_size=64", "--num_iter=90"]
      resources:
        limits:
          nvidia.com/gpu: 1
``` 

You should see the following results if you run the above file.

```
$ kubectl create -f resnet.yaml
pod/resnet-gpu-pod created

$ kubectl get pods resnet-gpu-pod
NAME             READY   STATUS    RESTARTS   AGE
resnet-gpu-pod   0/1     Running   0          17s 

$ kubectl logs resnet-gpu-pod -n default -f
PY 3.5.2 (default, Nov 23 2017, 16:37:01)
[GCC 5.4.0 20160609]
TF 1.8.0
Script arguments:
  --layers 50
  --display_every 10
  --iter_unit epoch
  --batch_size 64
  --num_iter 100
  --precision fp16
Training
WARNING:tensorflow:Using temporary folder as model directory: /tmp/tmpjw90ypze
2020-07-31 00:57:23.020712: I tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:898] successful NUMA node read from SysFS had negative value (-1), but there must be at least one NUMA node, so returning NUMA node zero
2020-07-31 00:57:23.023190: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1356] Found device 0 with properties:
name: Tesla T4 major: 7 minor: 5 memoryClockRate(GHz): 1.59
pciBusID: 0000:00:05.0
totalMemory: 14.73GiB freeMemory: 14.62GiB
2020-07-31 00:57:23.023226: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1435] Adding visible gpu devices: 0
2020-07-31 00:57:23.846680: I tensorflow/core/common_runtime/gpu/gpu_device.cc:923] Device interconnect StreamExecutor with strength 1 edge matrix:
2020-07-31 00:57:23.846743: I tensorflow/core/common_runtime/gpu/gpu_device.cc:929]      0
2020-07-31 00:57:23.846753: I tensorflow/core/common_runtime/gpu/gpu_device.cc:942] 0:   N
2020-07-31 00:57:23.847023: I tensorflow/core/common_runtime/gpu/gpu_device.cc:1053] Created TensorFlow device (/job:localhost/replica:0/task:0/device:GPU:0 with 14151 MB memory) -> physical GPU (device: 0, name: Tesla T4, pci bus id: 0000:00:05.0, compute capability: 7.5)
  Step Epoch Img/sec   Loss  LR
     1   1.0     3.1  7.936  8.907 2.00000
    10  10.0    68.3  1.989  2.961 1.65620
    20  20.0   214.0  0.002  0.978 1.31220
    30  30.0   213.8  0.008  0.979 1.00820
    40  40.0   210.8  0.095  1.063 0.74420
    50  50.0   211.9  0.261  1.231 0.52020
    60  60.0   211.6  0.104  1.078 0.33620
    70  70.0   211.3  0.340  1.317 0.19220
    80  80.0   206.7  0.168  1.148 0.08820
    90  90.0   210.4  0.092  1.073 0.02420
   100 100.0   210.4  0.001  0.982 0.00020
```

> [Note]
> To prevent workloads that do not require GPU from being allocated to GPU nodes, see [Taints and Tolerations](https://kubernetes.io/docs/concepts/scheduling-eviction/taint-and-toleration/).

### Autoscaler
Autoscaler is a feature that automatically adjusts the number of nodes when a node group does not have enough resources available to schedule pods or when the node's utilization remains below a certain level. Autoscaler can be set for each node group and operates independently of each other. This feature is based on the cluster-autoscaler feature, an officially supported feature of the Kubernetes project. For more information, refer to [Cluster Autoscaler](https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler).

> [Note]
> The version of the `cluster-autoscaler` applied to NHN Kubernetes Service (NKS) is `1.19.0.`

#### Glossary
Terms used in relation to the autoscaler and their meanings are as follows:

| Term | Meaning |
| --- | --- |
| Scale Up | Increase a number of nodes. |
| Scale Down | Decrease a number of nodes. |

> [Caution]
> If worker nodes are working in an environment with no Internet connection, autoscaler container images must be manually installed on the worker nodes. This task is required for the following targets:
> 
> * Pangyo Region: Node groups created before November 24, 2020
> * Pyeongchon Region: Node groups created before November 19, 2020
> 
> The container image path of autoscaler is as follows:
>
> * k8s.gcr.io/autoscaling/cluster-autoscaler:v1.19.0

#### Autoscaler Settings
Autoscaler is set and operated for each node group. Autoscaler can be set up in various ways, as listed below:

* Set up on the default node groups when creating a cluster.
* Set up on additional node groups when adding the node groups.
* Set up on existing node groups.

Activating the autoscaler enables the following options:

| Settings Item | Meaning | Valid Range | Default | Unit |
| --- | --- | --- | --- | --- |
| Minimum Node Count | Minimum number of nodes that can be scaled down| 1-10 | 1 | unit|
| Maximum Node Count | Maximum number of nodes that can be scaled up| 1-10 | 10 | unit|
| Scaling Down | Enable/Disable Node Scale-down | Enable/Disable | Enable | - |
| Scale Down Utilization Threshold | Reference value to determine resource usage threshold range for scale-down | 1-100 | 50 | % |
| Scale Down Unneeded Time| The duration for retaining resource usage of target nodes to scale down below the threshold| 1-1440 | 10 | minutes |
| Scale Down Delay After Add | Delay before starting to monitor for scale-down targets after scaling up| 10-1440 | 10 | minutes |

> [Caution]
> Nodes cannot be manually added to or deleted from node groups on which autoscaler is enabled.

#### Scale-up/down Conditions
Scales up if all of the following conditions are met:

* There are no more available nodes to schedule pods.
* The current number of nodes is below the maximum limit.

Scales down if all of the following conditions are met:

* Nodes use resources below the threshold for the set critical area duration.
* The current number of nodes exceeds the minimum limit.

If some nodes contain at least one pod that meets the following conditions, then they will be excluded from the list of nodes to be scaled down:

* Pods restricted by "PodDisruptionBudget"
* Pods in the "kube-system" namespace
* Pods not started by control objects such as "deployment" or "replicaset"
* Pods that use the local storage
* Pods that cannot be moved to other nodes because of the restrictions such as "node selector"

For more information on the conditions for scale-up/down, see [Cluster Autoscaler FAQ](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/FAQ.md).

#### Operation Example
Let's check how the autoscaler work through the following example:

##### 1. Enabling Autoscaler

Enables autoscaling on the default node group of the cluster you want. For this example, the number of nodes for the default group has been set to 1 and autoscaler settings are configured as follows:

| Settings Item | Value |
| --- | --- |
| Minimum Node Count | 1 |
| Maximum Node Count | 5 |
| Scaling Down | Enable |
| Scale Down Utilization Threshold | 50 |
| Scale Down Unneeded Time| 3 |
| Scale Down Delay After Add | 10 |

##### 2. Deploying Pods

Deploy pods using the following manifest:

> [Caution]
> Just like this manifest, all manifests must have a container resource request defined on them.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 15
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
        resources:
          requests:
            cpu: "100m"
```

Because the total amount of CPU resources for the requested pods is bigger than the resources that a single node can handle, some of the pods are left behind in the `Pending` status, as shown below. In this case, the nodes will scale up.

```
# kubectl get pods
NAME                               READY   STATUS    RESTARTS   AGE
nginx-deployment-756fd4cdf-5gftm   1/1     Running   0          34s
nginx-deployment-756fd4cdf-64gtv   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-7bsst   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-8892p   1/1     Running   0          34s
nginx-deployment-756fd4cdf-8k4cc   1/1     Running   0          34s
nginx-deployment-756fd4cdf-cprp7   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-cvs97   1/1     Running   0          34s
nginx-deployment-756fd4cdf-h7ftk   1/1     Running   0          34s
nginx-deployment-756fd4cdf-hv2fz   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-j789l   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-jrkfj   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-m887q   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-pvnfc   0/1     Pending   0          34s
nginx-deployment-756fd4cdf-wrj8b   1/1     Running   0          34s
nginx-deployment-756fd4cdf-x7ns5   0/1     Pending   0          34s
```

##### 3. Checking Node Scale-up

The following is the node list before scale-up:

```
# kubectl get nodes
NAME                                            STATUS   ROLES    AGE   VERSION
autoscaler-test-default-w-ohw5ab5wpzug-node-0   Ready    <none>   45m   v1.23.3
```

After 5-10 minutes, the nodes should be scaled up as shown below:

```
# kubectl get nodes
NAME                                            STATUS   ROLES    AGE   VERSION
autoscaler-test-default-w-ohw5ab5wpzug-node-0   Ready    <none>   48m   v1.23.3
autoscaler-test-default-w-ohw5ab5wpzug-node-1   Ready    <none>   77s   v1.23.3
autoscaler-test-default-w-ohw5ab5wpzug-node-2   Ready    <none>   78s   v1.23.3
```

The pods that were in `Pending` status are now normally scheduled after the scale-up.

```
# kubectl get pods -o wide
NAME                               READY   STATUS    RESTARTS   AGE     IP            NODE                                            NOMINATED NODE   READINESS GATES
nginx-deployment-756fd4cdf-5gftm   1/1     Running   0          4m29s   10.100.8.13   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
nginx-deployment-756fd4cdf-64gtv   1/1     Running   0          4m29s   10.100.22.5   autoscaler-test-default-w-ohw5ab5wpzug-node-1   <none>           <none>
nginx-deployment-756fd4cdf-7bsst   1/1     Running   0          4m29s   10.100.22.4   autoscaler-test-default-w-ohw5ab5wpzug-node-1   <none>           <none>
nginx-deployment-756fd4cdf-8892p   1/1     Running   0          4m29s   10.100.8.10   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
nginx-deployment-756fd4cdf-8k4cc   1/1     Running   0          4m29s   10.100.8.12   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
nginx-deployment-756fd4cdf-cprp7   1/1     Running   0          4m29s   10.100.12.7   autoscaler-test-default-w-ohw5ab5wpzug-node-2   <none>           <none>
nginx-deployment-756fd4cdf-cvs97   1/1     Running   0          4m29s   10.100.8.14   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
nginx-deployment-756fd4cdf-h7ftk   1/1     Running   0          4m29s   10.100.8.11   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
nginx-deployment-756fd4cdf-hv2fz   1/1     Running   0          4m29s   10.100.12.5   autoscaler-test-default-w-ohw5ab5wpzug-node-2   <none>           <none>
nginx-deployment-756fd4cdf-j789l   1/1     Running   0          4m29s   10.100.22.6   autoscaler-test-default-w-ohw5ab5wpzug-node-1   <none>           <none>
nginx-deployment-756fd4cdf-jrkfj   1/1     Running   0          4m29s   10.100.12.4   autoscaler-test-default-w-ohw5ab5wpzug-node-2   <none>           <none>
nginx-deployment-756fd4cdf-m887q   1/1     Running   0          4m29s   10.100.22.3   autoscaler-test-default-w-ohw5ab5wpzug-node-1   <none>           <none>
nginx-deployment-756fd4cdf-pvnfc   1/1     Running   0          4m29s   10.100.12.6   autoscaler-test-default-w-ohw5ab5wpzug-node-2   <none>           <none>
nginx-deployment-756fd4cdf-wrj8b   1/1     Running   0          4m29s   10.100.8.15   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
nginx-deployment-756fd4cdf-x7ns5   1/1     Running   0          4m29s   10.100.12.3   autoscaler-test-default-w-ohw5ab5wpzug-node-2   <none>           <none>
```

You can check scale-up events with the following command:

```
# kubectl get events --field-selector reason="TriggeredScaleUp"
LAST SEEN   TYPE     REASON             OBJECT                                 MESSAGE
4m          Normal   TriggeredScaleUp   pod/nginx-deployment-756fd4cdf-64gtv   pod triggered scale-up: [{default-worker-bf5999ab 1->3 (max: 5)}]
4m          Normal   TriggeredScaleUp   pod/nginx-deployment-756fd4cdf-7bsst   pod triggered scale-up: [{default-worker-bf5999ab 1->3 (max: 5)}]
...
```


##### 4. Checking Node Scale-down after Deleting Pods

Deleting the current deployments also deletes the deployed pods.

```
# kubectl get pods
NAME                               READY   STATUS        RESTARTS   AGE
nginx-deployment-756fd4cdf-5gftm   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-64gtv   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-7bsst   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-8892p   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-8k4cc   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-cprp7   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-h7ftk   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-hv2fz   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-j789l   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-jrkfj   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-m887q   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-pvnfc   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-wrj8b   0/1     Terminating   0          20m
nginx-deployment-756fd4cdf-x7ns5   0/1     Terminating   0          20m
#
# kubectl get pods
No resources found in default namespace.
#
```

After a while, you can see nodes are scaled down to 1. The time it takes to scale down may vary depending on your settings.

```
# kubectl get nodes
NAME                                            STATUS   ROLES    AGE   VERSION
autoscaler-test-default-w-ohw5ab5wpzug-node-0   Ready    <none>   71m   v1.23.3
```

You can check scale-down events with the following command:

```
# kubectl get events --field-selector reason="ScaleDown"
LAST SEEN   TYPE     REASON      OBJECT                                               MESSAGE
13m         Normal   ScaleDown   node/autoscaler-test-default-w-ohw5ab5wpzug-node-1   node removed by cluster autoscaler
13m         Normal   ScaleDown   node/autoscaler-test-default-w-ohw5ab5wpzug-node-2   node removed by cluster autoscaler
```

You can check the status of each node group's autoscaler through `configmap/cluster-autoscaler-status`. Configmaps are created in different namespaces per node group. The following is the naming convention for namespace per node group created by the autoscaler:

* Format: nhn-ng-{node group name}
* Enter a node group name in {node group name}.
* The default node group name is "default-worker."

The status of the default node group's autoscaler can be checked using the following method. For more information, see [Cluster Autoscaler FAQ](https://github.com/kubernetes/autoscaler/blob/master/cluster-autoscaler/FAQ.md).

```
# kubectl get configmap/cluster-autoscaler-status -n nhn-ng-default-worker -o yaml
apiVersion: v1
data:
  status: |+
    Cluster-autoscaler status at 2020-11-03 12:39:12.190150095 +0000 UTC:
    Cluster-wide:
      Health:      Healthy (ready=1 unready=0 notStarted=0 longNotStarted=0 registered=1 longUnregistered=0)
                   LastProbeTime:      2020-11-03 12:39:12.185954244 +0000 UTC m=+43.664545435
                   LastTransitionTime: 2020-11-03 12:38:41.705407217 +0000 UTC m=+13.183998415
      ScaleUp:     NoActivity (ready=1 registered=1)
                   LastProbeTime:      2020-11-03 12:39:12.185954244 +0000 UTC m=+43.664545435
                   LastTransitionTime: 2020-11-03 12:38:41.705407217 +0000 UTC m=+13.183998415
      ScaleDown:   NoCandidates (candidates=0)
                   LastProbeTime:      2020-11-03 12:39:12.185954244 +0000 UTC m=+43.664545435
                   LastTransitionTime: 2020-11-03 12:38:41.705407217 +0000 UTC m=+13.183998415

    NodeGroups:
      Name:        default-worker-f9a9ee5e
      Health:      Healthy (ready=1 unready=0 notStarted=0 longNotStarted=0 registered=1 longUnregistered=0 cloudProviderTarget=1 (minSize=1, maxSize=5))
                   LastProbeTime:      2020-11-03 12:39:12.185954244 +0000 UTC m=+43.664545435
                   LastTransitionTime: 2020-11-03 12:38:41.705407217 +0000 UTC m=+13.183998415
      ScaleUp:     NoActivity (ready=1 cloudProviderTarget=1)
                   LastProbeTime:      2020-11-03 12:39:12.185954244 +0000 UTC m=+43.664545435
                   LastTransitionTime: 2020-11-03 12:38:41.705407217 +0000 UTC m=+13.183998415
      ScaleDown:   NoCandidates (candidates=0)
                   LastProbeTime:      2020-11-03 12:39:12.185954244 +0000 UTC m=+43.664545435
                   LastTransitionTime: 2020-11-03 12:38:41.705407217 +0000 UTC m=+13.183998415

kind: ConfigMap
metadata:
  annotations:
    cluster-autoscaler.kubernetes.io/last-updated: 2020-11-03 12:39:12.190150095 +0000
      UTC
  creationTimestamp: "2020-11-03T12:38:28Z"
  name: cluster-autoscaler-status
  namespace: nhn-ng-default-worker
  resourceVersion: "1610"
  selfLink: /api/v1/namespaces/nhn-ng-default-worker/configmaps/cluster-autoscaler-status
  uid: e72bd1a2-a56f-41b4-92ee-d11600386558
```

> [Note]
> As for the status information, the `Cluster-wide` area has the same information as `NodeGroups.`

#### Example of an action working with HPA (HorizontalPodAutoscale)
Horizontal Pod Autoscaler (HPA) observes resource usage, such as CPU usage, to auto-scale the number of pods of ReplicationController, Deployment, ReplicaSet, and StatefulSet. As the number of pods is adjusted, there could be too many or too few resources available in the node. At this moment, utilize the Autoscaler feature to increase or decrease the number of nodes. In this example, we will see how HPA and Autoscaler can work together to deal with this issue. For more information on HPA, see [Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/). 

##### 1. Enabling Autoscaler
Enable Autoscaler as shown in the above example.

##### 2. Configuring HPA
Deploy a container that creates CPU load for a certain amount of time after receiving a web request. The, expose the service. The following is taken from the `php-apache.yaml` file.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: php-apache
spec:
  selector:
    matchLabels:
      run: php-apache
  replicas: 1
  template:
    metadata:
      labels:
        run: php-apache
    spec:
      containers:
      - name: php-apache
        image: k8s.gcr.io/hpa-example
        ports:
        - containerPort: 80
        resources:
          limits:
            cpu: 500m
          requests:
            cpu: 200m
---
apiVersion: v1
kind: Service
metadata:
  name: php-apache
  labels:
    run: php-apache
spec:
  ports:
  - port: 80
  selector:
    run: php-apache
```

```
# kubectl apply -f php-apache.yaml
deployment.apps/php-apache created
service/php-apache created
```

Now, set up HPA. For the php-apache deployment object just created in the previous step, set as follows: min pod count = 1, max pod count = 30, target CPU load = 50%.

```
# kubectl autoscale deployment php-apache --cpu-percent=50 --min=1 --max=30
horizontalpodautoscaler.autoscaling/php-apache autoscaled
```

If you look up the state of HPA, you can see the settings and the current state. Since no web request that causes CPU load has been sent yet, CPU load is still at 0%.

```
# kubectl get hpa
NAME         REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
php-apache   Deployment/php-apache   0%/50%    1         30        1          80s
```

##### 3. Authorizing Load
Now run the pod that triggers load in the new terminal. This pod sends web requests without stopping. You can stop this requesting action with `Ctrl+C`.

```
# kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://php-apache; done"
If you don't see a command prompt, try pressing enter.
OK!OK!OK!OK!OK!OK!OK!
```

Using the `kubectl top nodes` command, you can see the current resource usage of the node. You can observe the increase in CPU load as time goes after running the pod that causes load.

```
# kubectl top nodes
NAME                                            CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%
autoscaler-test-default-w-ohw5ab5wpzug-node-0   66m          6%     1010Mi          58%

(A moment later)

# kubectl top nodes
NAME                                            CPU(cores)   CPU%   MEMORY(bytes)   MEMORY%
autoscaler-test-default-w-ohw5ab5wpzug-node-0   574m         57%    1013Mi          58%
```

If you look up the status of HPA, you can see the increase in CPU load and the resultant increase in REPLICAS (number of pods).

```
# kubectl get hpa
NAME         REFERENCE               TARGETS    MINPODS   MAXPODS   REPLICAS   AGE
php-apache   Deployment/php-apache   250%/50%   1         30        5          2m44s
```

##### 4. Checking the operation of Autoscaler
If you look up pods, due to the increase in the number of pods, you can see some pods are running as they are scheduled to `node-0`, but some are still pending

```
# kubectl get pods -o wide
NAME                          READY   STATUS    RESTARTS   AGE     IP            NODE                                            NOMINATED NODE   READINESS GATES
load-generator                1/1     Running   0          2m      10.100.8.39   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
php-apache-79544c9bd9-6f7nm   0/1     Pending   0          65s     <none>        <none>                                          <none>           <none>
php-apache-79544c9bd9-82xkn   1/1     Running   0          80s     10.100.8.41   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
php-apache-79544c9bd9-cjj9q   0/1     Pending   0          80s     <none>        <none>                                          <none>           <none>
php-apache-79544c9bd9-k6nnt   1/1     Running   0          4m27s   10.100.8.38   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
php-apache-79544c9bd9-mplnn   0/1     Pending   0          19s     <none>        <none>                                          <none>           <none>
php-apache-79544c9bd9-t2knw   1/1     Running   0          80s     10.100.8.40   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
```

This situation of not being able to schedule pods is the node extension condition for Autoscaler. If you look up the state information provided by Cluster Autoscaler pod, you can see that ScaleUp is in InProgress state.

```
# kubectl get cm/cluster-autoscaler-status -n nhn-ng-default-worker -o yaml
apiVersion: v1
data:
  status: |+
    Cluster-autoscaler status at 2020-11-24 13:00:40.210137143 +0000 UTC:
    Cluster-wide:
      Health:      Healthy (ready=1 unready=0 notStarted=0 longNotStarted=0 registered=1 longUnregistered=0)
                   LastProbeTime:      2020-11-24 13:00:39.930763305 +0000 UTC m=+1246178.729396969
                   LastTransitionTime: 2020-11-10 02:51:14.353177175 +0000 UTC m=+13.151810823
      ScaleUp:     InProgress (ready=1 registered=1)
                   LastProbeTime:      2020-11-24 13:00:39.930763305 +0000 UTC m=+1246178.729396969
                   LastTransitionTime: 2020-11-24 12:58:34.83642035 +0000 UTC m=+1246053.635054003
      ScaleDown:   NoCandidates (candidates=0)
                   LastProbeTime:      2020-11-24 13:00:39.930763305 +0000 UTC m=+1246178.729396969
                   LastTransitionTime: 2020-11-20 01:42:32.287146552 +0000 UTC m=+859891.085780205

    NodeGroups:
      Name:        default-worker-bf5999ab
      Health:      Healthy (ready=1 unready=0 notStarted=0 longNotStarted=0 registered=1 longUnregistered=0 cloudProviderTarget=2 (minSize=1, maxSize=3))
                   LastProbeTime:      2020-11-24 13:00:39.930763305 +0000 UTC m=+1246178.729396969
                   LastTransitionTime: 2020-11-10 02:51:14.353177175 +0000 UTC m=+13.151810823
      ScaleUp:     InProgress (ready=1 cloudProviderTarget=2)
                   LastProbeTime:      2020-11-24 13:00:39.930763305 +0000 UTC m=+1246178.729396969
                   LastTransitionTime: 2020-11-24 12:58:34.83642035 +0000 UTC m=+1246053.635054003
      ScaleDown:   NoCandidates (candidates=0)
                   LastProbeTime:      2020-11-24 13:00:39.930763305 +0000 UTC m=+1246178.729396969
                   LastTransitionTime: 2020-11-20 01:42:32.287146552 +0000 UTC m=+859891.085780205
...
```

After a while, you can see another node (node-8) has been added.

```
# kubectl get nodes
NAME                                            STATUS     ROLES    AGE   VERSION
autoscaler-test-default-w-ohw5ab5wpzug-node-0   Ready      <none>   22d   v1.23.3
autoscaler-test-default-w-ohw5ab5wpzug-node-8   Ready      <none>   90s   v1.23.3
```

You can see all pods that were in Pending state are properly scheduled and now in the Running state.

```
# kubectl get pods -o wide
NAME                          READY   STATUS    RESTARTS   AGE     IP            NODE                                            NOMINATED NODE   READINESS GATES
load-generator                1/1     Running   0          5m32s   10.100.8.39   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
php-apache-79544c9bd9-6f7nm   1/1     Running   0          4m37s   10.100.42.3   autoscaler-test-default-w-ohw5ab5wpzug-node-8   <none>           <none>
php-apache-79544c9bd9-82xkn   1/1     Running   0          4m52s   10.100.8.41   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
php-apache-79544c9bd9-cjj9q   1/1     Running   0          4m52s   10.100.42.5   autoscaler-test-default-w-ohw5ab5wpzug-node-8   <none>           <none>
php-apache-79544c9bd9-k6nnt   1/1     Running   0          7m59s   10.100.8.38   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
php-apache-79544c9bd9-mplnn   1/1     Running   0          3m51s   10.100.42.4   autoscaler-test-default-w-ohw5ab5wpzug-node-8   <none>           <none>
php-apache-79544c9bd9-t2knw   1/1     Running   0          4m52s   10.100.8.40   autoscaler-test-default-w-ohw5ab5wpzug-node-0   <none>           <none>
```

If you press `Ctrl+C` to stop the pod (`load-generator`) that was executed for load, load will decrease after a while. The lower the load, the lower the CPU usage occupied by the pod, which in return decrease the number of pods.

```
# kubectl get hpa
NAME         REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE
php-apache   Deployment/php-apache   0%/50%    1         30        1          31m
```

As the number of pods decreases, the resource usage of the node also decreases, which results in the reduction in nodes. You can see the newly added node-8 has been reduced.

```
# kubectl get nodes
NAME                                            STATUS   ROLES    AGE   VERSION
autoscaler-test-default-w-ohw5ab5wpzug-node-0   Ready    <none>   22d   v1.23.3
```


### User Script (old)
You can register a user script when creating clusters and additional node groups. A user script has the following features.

* Feature setting
    * This feature can be set by worker node group.
    * A user script entered when creating clusters is applied to the default worker node group.
    * A user script entered when creating additional node groups is applied to the corresponding worker node group.
    * **The content of a user script cannot be changed after the worker node group is created.**
        * Note, what is changed in a user script applies to the nodes created after the change of the user script.
* Script execution time
    * A user script is executed during the instance initialization process while initializing the worker node.
    * After the user script has been executed, it sets and registers the instance as the worker node of the 'worker node group'.
* Script content
    * The first line of a user script must start with #!.
    * The maximum size of script is 64KB.
    * The script is run with the root permission.
    * The script execution records are stored in the following location.
        * Script exit code: `/var/log/userscript.exitcode`
        * Standard output and standard error streams of script: `/var/log/userscript.output`

### User Script
The features of a new version of user script are included in the node groups created after July 26, 2022. The following features are found in the new version.

* **You can change the user script content after the worker node group is created.**
* The script execution records are stored in the following location.
    * Script exit code: `/var/log/userscript_v2.exitcode`
    * Standard output and standard error streams of scrip: `/var/log/userscript_v2.output`

* Correlations with the old version
    * Features of the new version replace those of the old version.
        * The user script set when creating node groups through the console and API is configured for the new version.
    * For the worker node group that set the old version of a user script, the old version and new version features work separately.
        * You cannot change the user script content set in the old version.
        * You can change the user script content set in the new version.
    * If user scripts are set in the old version and the new version respectively, they are executed in the following order.
        1. The old version of a user script
        2. The new version of a user script

## Cluster Management
To run and manage clusters from a remote host, `kubectl` is required, which is the command-line tool (CLI) provided by Kubernetes.

### Installing kubectl
You can use kubectl by downloading an executable file without any special installation process. The download path for each operating system is as follows.

| OS | Download Command |
| --- | --- |
| Linux | curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.7/bin/linux/amd64/kubectl |
| MacOS | curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.7/bin/darwin/amd64/kubectl |
| Windows | curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.15.7/bin/windows/amd64/kubectl.exe |

For more details on installation and options, see [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

#### Change Permission
The downloaded file does not have the execute permission by default. You need to add the execute permission.

```
$ chmod +x kubectl
```

#### Change the Location or Set the Path
Move the file to the path set in the environment variable so that kubectl can be executed on any path, or add the path including kubectl to the environment variable.

* Change the location to a path set in the environment variable
```
$ sudo mv kubectl /usr/local/bin/
```

* Add the path to the environment variable
```
// Executed on the path including kubectl
$ export PATH=$PATH:$(pwd)
```

### Configuration
To access Kubernetes cluster with kubectl, cluster configuration file (kubeconfig) is required. On the NHN Cloud web console, open the **Container > NHN Kubernetes Service (NKS)** page and select a cluster to access. From **Basic Information**, click **Download** of **Configuration Files** to download a configuration file. Move the downloaded configuration file to a location of your choice to serve it as a reference for kubectl execution.

> [Caution]
> A configuration file downloaded from the NHN Cloud web console includes cluster information and token for authentication. With the file, you're authorized to access corresponding Kubernetes clusters. Take cautions for not losing configuration files.

kubectl requires a cluster configuration file every time it is executed, so a cluster configuration file must be specified by using the `--kubeconfig` option. However, if the environment variable includes specific path for a cluster configuration file, there is no need to specify each option.

```
$ export KUBECONFIG={Path of cluster configuration file}
```

You may copy cluster configuration file path to `$HOME/.kube/config`, which is the default configuration file of kubectl, if you don't want to save it to an environment variable. However, when there are many clusters, it is easier to change environment variables.

### Confirming Connection
See if it is well set by the `kubectl version` command. If there's no problem, `Server Version` is printed.

```
$ kubectl version
Client Version: version.Info{Major:"1", Minor:"15", GitVersion:"v1.15.7", GitCommit:"6c143d35bb11d74970e7bc0b6c45b6bfdffc0bd4", GitTreeState:"clean", BuildDate:"2019-12-11T12:42:56Z", GoVersion:"go1.12.12", Compiler:"gc", Platform:"darwin/amd64"}
Server Version: version.Info{Major:"1", Minor:"15", GitVersion:"v1.15.7", GitCommit:"6c143d35bb11d74970e7bc0b6c45b6bfdffc0bd4", GitTreeState:"clean", BuildDate:"2019-12-11T12:34:17Z", GoVersion:"go1.12.12", Compiler:"gc", Platform:"linux/amd64"}
```

* Client Version: Version information of executed kubectl file
* Server Version: Kubernetes version information comprising a cluster

### CSR (CertificateSigningRequest)
Using Certificate API of Kubernetes, you can request and issue the X.509 certificate for a Kubernetes API client . CSR resource lets you request certificate and decide to accept/reject the request. For more information, see the [Certificate Signing Requests](https://kubernetes.io/docs/reference/access-authn-authz/certificate-signing-requests/) document.

#### CSR Request and Issue Approval Example
First of all, create a private key. For more information on certificate creation, see the [Certificates](https://kubernetes.io/docs/concepts/cluster-administration/certificates/) document.

```
# openssl genrsa -out dev-user1.key 2048
Generating RSA private key, 2048 bit long modulus
...........................................................................+++++
..................+++++
e is 65537 (0x010001)

# openssl req -new -key dev-user1.key -subj "/CN=dev-user1" -out dev-user1.csr
```

Create a CSR resource that includes created private key information and request certificate issuance.

```
# BASE64_CSR=$(cat dev-user1.csr | base64 | tr -d '\n')
# cat <<EOF > csr.yaml -
apiVersion: certificates.k8s.io/v1beta1
kind: CertificateSigningRequest
metadata:
  name: dev-user1
spec:
  groups:
  - system:authenticated
  request: ${BASE64_CSR}
  usages:
  - digital signature
  - key encipherment
  - server auth
  - client auth
EOF

# kubectl apply -f csr.yaml
certificatesigningrequest.certificates.k8s.io/dev-user1 created
```

The registered CSR is in `Pending` state. This state indicates waiting for issuance approval or rejection.

```
# kubectl get csr
NAME        AGE   REQUESTOR          CONDITION
dev-user1   6s    system:unsecured   Pending
```

Approve this certificate issuance request.

```
# kubectl certificate approve dev-user1
certificatesigningrequest.certificates.k8s.io/dev-user1 approved
```

If you check the CSR again, you can see that it has been changed to the `Approved,Issued` state.
```
# kubectl get csr
NAME        AGE    REQUESTOR          CONDITION
dev-user1   114s   system:unsecured   Approved,Issued
```

You can look up the certificate as below. The certificate is a value for the Certificate field under Status.

```
# kubectl get csr/dev-user1 -o yaml
apiVersion: certificates.k8s.io/v1beta1
kind: CertificateSigningRequest
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: |
      {"apiVersion":"certificates.k8s.io/v1beta1","kind":"CertificateSigningRequest","metadata":{"annotations":{},"name":"dev-user1"},"spec":{"groups":["system:authenticated"],"request":"LS0tLS...((omitted))","usages":["digital signature","key encipherment","server auth","client auth"]}}
  creationTimestamp: "2020-12-07T06:32:53Z"
  name: dev-user1
  resourceVersion: "3202"
  selfLink: /apis/certificates.k8s.io/v1beta1/certificatesigningrequests/dev-user1
  uid: b22477eb-0abc-4fc4-8a79-f6516751a940
spec:
  groups:
  - system:masters
  - system:authenticated
  request: LS0tLS...((omitted))
  usages:
  - digital signature
  - key encipherment
  - server auth
  - client auth
  username: system:unsecured
status:
  certificate: LS0tLS...((omitted))
  conditions:
  - lastUpdateTime: "2020-12-07T06:34:43Z"
    message: This CSR was approved by kubectl certificate approve.
    reason: KubectlApprove
    type: Approved
```

> [Caution]
> This feature is provided only when the time of cluster creation falls within the following period:
> 
> * Pangyo region: Cluster created on December 29, 2020 or later
> * Pyeongchon region: Cluster created on December 24, 2020 or later

### Admission Controller plugin
The admission controller can intercept a Kubernetes API server request and change objects or deny the request. See [Admission Controller]( https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/) for more information about the admission controller. For usage examples of the admission controller, see [Admission Controller Guide](https://kubernetes.io/blog/2019/03/21/a-guide-to-kubernetes-admission-controllers/).

The type of plugin applied to the admission controller varies depending on the cluster version and the time of cluster creation. For more information, see the list of plugins available depending on the time of cluster creation by region.

#### v1.19.13 or earlier
The following applies to clusters created on February 22, 2021 or earlier for the Pangyo region and clusters created on February 17, 2021 or earlier for the Pyeongchon region.

* DefaultStorageClass
* DefaultTolerationSeconds
* LimitRanger
* MutatingAdmissionWebhook
* NamespaceLifecycle
* NodeRestriction
* ResourceQuota
* ServiceAccount
* ValidatingAdmissionWebhook

The following applies to clusters created on February 23, 2021 or later for the Pangyo region and clusters created on February 18, 2021 or later for the Pyeongchon region.

* DefaultStorageClass
* DefaultTolerationSeconds
* LimitRanger
* MutatingAdmissionWebhook
* NamespaceLifecycle
* NodeRestriction
* PodSecurityPolicy (newly added)
* ResourceQuota
* ServiceAccount
* ValidatingAdmissionWebhook

#### v1.20.12 or later
All default active admission controllers per Kubernetes version are enabled. The following controllers are activated in addition to the default active admission controllers.
* NodeRestriction
* PodSecurityPolicy


### Cluster upgrade
NHN Kubernetes Service (NKS) supports the Kubernetes component upgrade for the currently operating Kubernetes clusters. 

#### Policy of supporting different Kubernetes versions
Kubernetes version is represented as `x.y.z`. `x` is the major, `y` is the minor, and `z` is the patch version. If features are added, it is a major or minor version upgrade. If it provides features compatible with previous versions such as bug fixes, it is a patch version. For more information about this, see [Semantic Versioning 2.0.0](https://semver.org/).

Kubernetes clusters can upgrade the Kubernetes components while in operation. To this end, each Kubernetes component defines whether to support the features based on the Kubernetes version difference. In minor version, for example, the difference of one version supports the Kubernetes component upgrade for the operating clusters by supporting the mutual feature compatibility. It also defines the upgrade sequence for each type of the components. For more information, see [Version Skew Policy](https://kubernetes.io/releases/version-skew-policy/).

#### Feature Behavior
Explains how the Kubernetes cluster upgrade feature supported by NHN Cloud works. 

##### Kubernetes Version Control
NHN Cloud's Kubernetes cluster controls the Kubernetes versions per cluster master and worker node group. Master's Kubernetes version can be checked in the cluster view screen, and the Kubernetes version of the worker node group can be checked in the screen view of each worker node group. 

##### Upgrade Rules
When upgrading, NHN Cloud's Kubernetes Cluster version control and Kubernetes versioning support policy must be followed to keep the proper sequence. The following rules are applied to NHN Cloud's Kubernetes cluster upgrade features.

* Upgrade commands must be given to each master and worker node group. 
* In order to upgrade, the Kubernetes version of the master and all worker node groups must match.
* Master must be upgraded first in order to upgrade the worker node group. 
* Can be upgraded to the next version of the current version (minor version+1). 
* Downgrade is not supported. 
* If the cluster is being updated due to the operation of other features, upgrade cannot be proceeded. 

The following table shows whether upgrade is possible while upgrading the Kubernetes version. The following conditions are used for the example: 

* List of Kubernetes versions supported by NHN Cloud: v1.21.6, v1.22.3, v1.23.3
* Clusters are created as v1.21.6

| Status | Master version | Whether master can be upgraded | Worker node group version | Whether worker node group can be upgraded
| --- | :-: | :-: | :-: | :-: |
| Initial state| v1.21.6 | Possible (Note 1) | v1.21.6 | Not possible (Note 2) | 
| State after master upgrade | v1.22.3 | Not possible (Note 3) | v1.21.6 | Possible (Note 4) | 
| State after worker node group upgrade | v1.22.3 | Possible (Note 1) | v1.22.3 | Not possible (Note 2) |
| State after master upgrade | v1.23.3 | Not possible (Note 3) | v1.22.3 | Possible (Note 4) | 
| State after worker node group upgrade | v1.23.3 | Not possible (Note 5) | v1.23.3 | Not possible (Note 2) |

Notes

* (Note 1) Upgrade is possible because the versions of the master and all worker node groups are matching
* (Note 2) Worker node groups can be upgraded once the master is upgraded
* (Note 3) The versions of the master and all worker node groups must match in order to upgrade
* (Note 4) Upgrade is possible because the master is upgraded
* (Note 5) Upgrade is not possible because the latest version supported by NHN Cloud is being used


##### Upgrading master components
NHN Cloud's Kubernetes cluster master consists of a number of masters to ensure high availability. Since upgrade is carried out by taking the rolling update method for the master, the availability of the clusters is guaranteed. 

In this process, the following might happen:

* Kubernetes API can fail temporarily.


##### Upgrading worker components
Worker components can be upgraded for each worker node group. Worker components are upgraded in the following steps:

1. Deactivate the cluster auto scaler feature. (Note 1)
2. Add a buffer node② to the worker node group.③
3. Perform the following tasks for all worker nodes within the worker node group④ :
    1. Evict the working pods from the worker node, and make the nodes not schedulable.
    2. Upgrade worker components.
    3. Make the nodes schedulable.
4. Evict working pods from the buffer node, and delete the buffer node.
5. Reactivate the cluster auto scaler feature. (Note 1)


Notes

* (Note 1) This step is valid only if the cluster autoscaler feature is enabled before starting the upgrade feature.
* (Note 2) Buffer node is an extra node which is created so that the pods evicted from existing worker nodes can be rescheduled during the upgrade process. It is created having the same scale as the worker node defined in that worker node group, and is automatically deleted when the upgrade process is over. This node is charged based on the instance fee policy. 
* ③ You can define the number of buffer nodes during upgrade. The default value is 1, and buffer nodes are not added when set to 0. Minimum value of 0, maximum value of (maximum number of nodes per node group - the current number of nodes for the worker node group).
* ④ Tasks are executed by the maximum number of unavailable nodes set during upgrade. The default value of 1, minimum value of 1, and maximum value of the current number of nodes for the worker node group.
In this process, the following might happen:

* Pods in service will be evicted and scheduled to another node. (To find out more about pod eviction, refer to the notes below.)
* Autoscaler feature does not work. 


> [Pod eviction cautions]
> 1. Pods operated by daemonset controller are not evicted.
> Daemonset controller runs the pod for each worker node, so the pods run by Daemonset controller cannot run in other nodes. While upgrading the worker node group, the pods run by the Daemonset controller will not be evicted. 
> 2. Pods that use the local storage will lose the previous data as they are evicted.
> Pods that use the local storage of the node by using `emptyDir` will lose the previous data when being evicted. This is because the storage space in the local node cannot be relocated to another node. 
> 3. Pods that cannot be copied to another node will not be relocated to another node.
> If the pods run by controllers such as (ReplicationController), (ReplicaSet), (Job), (Daemonset), and (StatefulSet) are evicted, they will be rescheduled to another node by the controller. However, the pods not run by these controllers will not be scheduled to another node after being evicted. 
> 4. Eviction can fail or slow down due to the PodDisruptionBudgets (PDB) setting.
> You can define the number of pods to maintain with the PodDisruptionBudgets(PDB) setting. Depending on how this setting is set, it may not be possible to evict pods or evicting pods can take longer than normal during upgrade. If pod eviction fails, upgrade fails as well. So if the PDB is enabled, appropriate PDB setting will ensure proper pod eviction. To find out more about PDB setting, see [here](https://kubernetes.io/docs/tasks/run-application/configure-pdb/).


To find out more about safely evicting pods, see [Safely Drain a Node](https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/).

##### System Pod Upgrade
If the versions match after upgrading the versions of the master and all worker node groups, the system pod which runs for Kubernetes cluster configuration will be upgraded.

> [Caution]
> If you do not upgrade the worker node group after upgrading the master, some pods might not work properly.

## LoadBalancer Service
Pod is a basic execution unit of a Kubernetes application and it is connected to a cluster network via CNI (Container Network Interface). By default, pods are not accessible from outside the cluster. To expose a pod's services to the outside of the cluster, you need to create a path to expose to the outside using the Kubernetes `LoadBalancer` Service object. Creating a LoadBalancer service object creates an NHN Cloud Load Balancer outside the cluster and associates it with the service object.

### Creating Web Server Pods
Write a deployment object manifest file that executes two nginx pods as follows and create an object.

```yaml
# nginx.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

With deployment object created, pods defined at manifest are automatically created.

```
$ kubectl apply -f nginx.yaml
deployment.apps/nginx-deployment created

$ kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE  
nginx-deployment-7fd6966748-pvrzs   1/1     Running   0          4m13s
nginx-deployment-7fd6966748-wv7rd   1/1     Running   0          4m13s
```

To use images stored in NHN Cloud Container Registry, you must first create a secret to log in to the user registry.
To use NHN Cloud (Old) Container Registry, you need to create a secret as follows:

```
$ kubectl create secret docker-registry registry-credential --docker-server={user registry address} --docker-username={email address for NHN Cloud account} --docker-password={service Appkey or integrated Appkey}
secret/registry-credential created

$ kubectl get secrets
NAME                  TYPE                             DATA   AGE
registry-credential   kubernetes.io/dockerconfigjson   1      30m
```


To use NHN Cloud Container Registry, you need to create a secret as follows:

```
$ kubectl create secret docker-registry registry-credential --docker-server={User registry address} --docker-username={User Access Key ID} --docker-password={Secret Access Key}
secret/registry-credential created

$ kubectl get secrets
NAME                  TYPE                             DATA   AGE
registry-credential   kubernetes.io/dockerconfigjson   1      30m
```


By adding secret information to the deployment manifest file and changing the name of image, pods can be created by using images saved at user registry.

```yaml
# nginx.yaml
...
spec:
  ...
  template:
    ...
    spec:
      containers:
      - name: nginx
        image: {User registry address}/nginx:1.14.2
        ...
      imagePullSecrets:
      - name: registry-credential

```

> [Note]
> Regarding how to use NHN Cloud Container Registry, see [User Guide for Container Registry](/Container/NCR/zh/user-guide).

### Creating LoadBalancer
To define service object of Kubernetes, a manifest comprised of the following items is required:

| Item | Description |
| --- | --- |
| metadata.name | Name of service object |
| spec.selector | Name of pod to be associated with service object |
| spec.ports | Interface setting to deliver incoming traffic from external load balancer to a pod |
| spec.ports.name | Name of interface |
| spec.ports.protocol | Protocol for an interface (e.g: TCP) |
| spec.ports.port | Port number to be made public out of service object |
| spec.ports.targetPort | Port number of a pod to be associated with service object |
| spec.type | Type of service object |

Service manifest is written like below. The LoadBalancer service object is associated with a pod labelled as `app: nginx`, following the defined name at **spec.selector**. And as **spec.ports** defines, traffic inflow via TCP/8080 is delivered to the TCP/80 port of the pod.

```yaml
# service.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-svc
  labels:
    app: nginx
spec:
  ports:
  - port: 8080
    targetPort: 80
    protocol: TCP
  selector:
    app: nginx
  type: LoadBalancer
```

When the LoadBalancer service object is created, it takes some time to create and associate a load balancer externally. Before associated with external load balancer, **EXTERNAL-IP** shows `<pending>`.

```
$ kubectl apply -f service.yaml
service/nginx-svc created

$ kubectl get service
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
nginx-svc    LoadBalancer   10.254.134.18   <pending>     8080:30013/TCP   11s
```

When it is associated with external load balancer, **EXTERNAL-IP** shows IP, which refers to floating IP of external load balancer.

```
$ kubectl get service
NAME         TYPE           CLUSTER-IP      EXTERNAL-IP      PORT(S)          AGE
nginx-svc    LoadBalancer   10.254.134.18   123.123.123.30   8080:30013/TCP   3m13s
```

> [Note]
> You can view the created load balancer on the **Network > Load Balancer** page.
> Load balancer IP is a floating IP allowing external access. You can check it on the **Network > Floating IP** page.


### Testing Service on Internet
Send an HTTP request via floating IP associated with load balancer to see if the web server pod of a Kubernetes cluster responds. Since the TcP/8080 port of a service object is attached to TCP/80 port of a pod, request must be sent to the TCP/8080 port. If external load balancer, service object, and pod are well associated, the web server shall respond to nginx default page.

```
$ curl http://123.123.123.30:8080
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

### Setting Detailed Options for Load Balancer
When defining service objects in Kubernetes, you can set several options for the load balancer.

#### Global Setting and Per-Listener Setting
For each setting item, global setting or per-listener setting is supported. If neither global nor per-listener setting is available, the default value for each setting is used.
* Per-listener setting: A setting that applies only to the target listener.
* Global setting: If the target listener doesn't have a per-listener setting, this setting is applied.

#### Format of Per-Listener Setting
Per-listener settings can be set by appending a prefix representing the listener to the global settings key. The prefix representing the listener is the service object's port protocol (`spec.ports[].protocol`) and port number (`spec.ports[].port`) concatenated with a dash (`-`). For example, if the protocol is TCP and the port number is 80, the prefix is ​​`TCP-80`. If you want to set session affinity for the listener associated with this port, you can set it in TCP-80.loadbalancer.nhncloud/pool-session-persistence under .metadata.annotations.

The manifest below is an example of mixing the global setting and per-listener settings. 

```yaml
apiVersion: v1
kind: Service
metadata:
  name: echosvr-svc
  labels:
    app: echosvr
  annotations:
    # Global setting
    loadbalancer.nhncloud/pool-lb-method: SOURCE_IP
    
    # Per-listener settings
    TCP-80.loadbalancer.nhncloud/pool-session-persistence: "SOURCE_IP"
    TCP-80.loadbalancer.nhncloud/listener-protocol: "HTTP"
    TCP-443.loadbalancer.nhncloud/pool-lb-method: LEAST_CONNECTIONS
    TCP-443.loadbalancer.nhncloud/listener-protocol: "TCP"
spec:
  ports:
  - name: tcp-80
    port: 80
    targetPort: 8080
    protocol: TCP
  - name: tcp-443
    port: 443
    targetPort: 8443
    protocol: TCP
  selector:
    app: echosvr
  type: LoadBalancer
```

When this manifest is applied, the per-listener settings are set as shown in the following table.

| Item | TCP-80 listener | TCP-433 listener| Description |
| --- | --- | --- | --- |
| Load Balancing Method | SOURCE_IP | LEAST_CONNECTIONS | TCP-80 listener is set to SOURCE_IP according to the global setting<br>TCP-443 listener is set to LEAST_CONNECTIONS according to the per-listener setting  |
| Session Affinity | SOURCE_IP | None | TCP-80 listener is set to SOURCE_IP according to the per-listener setting<br>TCP-443 listener is set to None by the default value |
| Listener Protocol | HTTP | TCP | Both the TCP-80 listener and the TCP-443 listener are set according to the per-listener settings   |

> [Note]
> The features without additional version information are only applicable to clusters of Kubernetes v1.19.13 or later.
> For clusters of Kubernetes v1.19.13 version, per-listener settings apply only to clusters created on January 25, 2022 or after.
>

> [Caution]
> All setting values for the features below must be entered in string format. In the YAML file input format, to enter in string format regardless of the input value, enclose the input value in double quotation marks ("). For more information about the YAML file format, see [Yaml Cookbook](https://yaml.org/YAML_for_ruby.html).
>


#### Set the session affinity
You can set the session affinity for the load balancer.

* The setting location is loadbalancer.nhncloud/pool-session-persistence under .metadata.annotations.
* Per-listener settings can be applied.
* It can be set to one of the following:
    * Empty string (""): Set session affinity to 'None'. The default when not set.
    * SOURCE_IP: Set session affinity to SOURCE_IP.
* If the load balancing method is SOURCE_IP, the session affinity setting is ignored, and the session affinity setting is set to None.
* Clusters of v1.17.6, v1.18.19
    * Changes cannot be made after the load balancer is created.
* Clusters of v1.19.13 or later
    * The setting can be changed even after the load balancer is created.

#### Set whether to keep a floating IP address when deleting the load balancer
The load balancer has a floating IP associated with it. You can set whether to delete or keep the floating IP associated with the load balancer when deleting the load balancer.

* The setting location is loadbalancer.openstack.org/keep-floatingip under .metadata.annotations.
* **Per-listener settings cannot be applied.**
* It can be set to one of the following:
    * true: Keep the floating IP.
    * false: Delete the floating IP. The default when not set.

> [Caution]
> v1.18.19 clusters created before October 26, 2021 have an issue where floating IPs are not deleted when the load balancer is deleted. If you contact us through 1:1 inquiry of the Customer Center, we will provide detailed information on the procedure to solve this issue.

#### Set the load balancer IP
You can set the load balancer IP when creating a load balancer.

* The setting location is .spec.loadBalancerIP.
* It can be set to one of the following.
  * Empty string(""): Associate an automatically created floating IP with the load balancer. The default when not set.
  * <Floating_IP>: Associate the existing floating IP with the load balancer. It can be used when there is a floating IP that is allocated and not associated. 

The following is an example of manifest for associating a custom floating IP to the load balancer.

```yaml
# service-fip.yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-svc-floatingIP
  labels:
    app: nginx
spec:
  loadBalancerIP: <Floating_IP>
  ports:
  - port: 8080
    targetPort: 80
    protocol: TCP
  selector:
    app: nginx
  type: LoadBalancer
```

#### Set whether to use the floating IP
You can set whether to use floating IPs when creating the load balancer.

* The setting location is service.beta.kubernetes.io/openstack-internal-load-balancer under .metadata.annotaions.
* It can be set to one of the following.
  * true: Use a VIP (Virtual IP), not a floating IP.
  * false: Use a floating IP. The default when not set.
* If you are using a VIP, you can specify the VIP to connect to the load balancer instead of the automatically created VIP by setting the .spec.loadBalancerIP entry together.

The following is an example of manifest for associating a custom VIP with the load balancer.

```yaml
# service-vip.yaml
apiVersion: v1
kind: Service
metadata:
 name: nginx-svc-fixedIP
 labels:
   app: nginx
 annotations:
   service.beta.kubernetes.io/openstack-internal-load-balancer: "true"
spec:
 loadBalancerIP: <Virtual_IP>
 ports:
 - port: 8080
   targetPort: 80
   protocol: TCP
 selector:
   app: nginx
 type: LoadBalancer
```

Depending on the combination of floating IP usage and load balancer IP setting, it works as follows.

| Floating IP Usage | Load balancer IP Setting | Description |
| --- | --- | --- |
| false | not set | Associate a floating IP with the load balancer. |
| false | set | Associate a specified floating IP with the load balancer. |
| true | not set | Automatically set a VIP associated with the load balancer. |
| true | set | Associate a specified VIP with the load balancer. |


#### Set the listener connection limit
You can set the connection limit for a listener.

* The setting location is loadbalancer.nhncloud/connection-limit under .metadata.annotations.
* Per-listener settings can be applied.
* Clusters of v1.17.6, v1.18.19
    * Minimum value of 1, maximum value of 60000. 
    * It you do not set it, it is set to -1, and the value applied to the actual load balancer is 2000.
* Clusters of v1.19.13 or later
    * Minimum value of 1, maximum value of 60000. 
    * If not set or a value out of range is entered, it is set to the default value of 60000.


#### Set the listener protocol
You can set the protocol of the listener.

* The setting location is loadbalancer.nhncloud/listener-protocol under .metadata.annotations.
* Per-listener settings can be applied.
* It can be set to one of the following:
    * TCP: The default when not set.
    * HTTP
    * HTTPS
    * TERMINATED_HTTPS: Set it to TERMINATED_HTTPS. SSL version, certificate, and private key information must be set additionally.

> [Caution]
> The listener protocol setting is not applied to the load balancer even if you change the service object.
> To change the listener protocol setting, you must delete the service object and then create it again.
> Note that the load balancer is deleted and then re-created in this case.


The SSL version can be set as follows:

* The setting location is loadbalancer.nhncloud/listener-terminated-https-tls-version under .metadata.annotations.
* Per-listener settings can be applied.
* It can be set to one of the following:
    * TLSv1.3: The default when not set.
    * TLSv1.2
    * TLSv1.1
    * TLSv1.0_2016
    * TLSv1.0
    * SSLv3

> [Caution]
> TLSv1.3 can be set in clusters created after March 29, 2022.

Certificate information can be set as follows:

* The setting location is loadbalancer.nhncloud/listener-terminated-https-cert under .metadata.annotations.
* Per-listener settings can be applied.
* It must include start and end lines.

Private key information can be set as follows:

* The setting location is loadbalancer.nhncloud/listener-terminated-https-key under .metadata.annotations.
* Per-listener settings can be applied.
* It must include start and end lines.

The following is an example of manifest for setting the listener protocol to TERMINATED_HTTPS. Certificate information and private key information are partially omitted.
```yaml
metadata:
  name: echosvr-svc
  labels:
    app: echosvr
  annotations:
    loadbalancer.nhncloud/listener-protocol: TERMINATED_HTTPS
    loadbalancer.nhncloud/listener-terminated-https-tls-version: TLSv1.2
    loadbalancer.nhncloud/listener-terminated-https-cert: |
      -----BEGIN CERTIFICATE-----
      MIIDZTCCAk0CCQDVfXIZ2uxcCTANBgkqhkiG9w0BAQUFADBvMQswCQYDVQQGEwJL
      ...
      fnsAY7JvmAUg
      -----END CERTIFICATE-----
    loadbalancer.nhncloud/listener-terminated-https-key: |
      -----BEGIN RSA PRIVATE KEY-----
      MIIEowIBAAKCAQEAz+U5VNZ8jTPs2Y4NVAdUWLhsNaNjRWQm4tqVPTxIrnY0SF8U
      ...
      u6X+8zlOYDOoS2BuG8d2brfKBLu3As5VAcAPLcJhE//3IVaZHxod
      -----END RSA PRIVATE KEY-----
```

#### Set the load balancing method
You can set the load balancing method.

* The setting location is loadbalancer.nhncloud/pool-lb-method under .metadata.annotations.
* Per-listener settings can be applied.
* It can be set to one of the following:
    * ROUND_ROBIN: The default when not set.
    * LEAST_CONNECTIONS
    * SOURCE_IP


#### Set the health check protocol
You can set the health check protocol.

* The setting location is loadbalancer.nhncloud/healthmonitor-type under .metadata.annotations.
* Per-listener settings can be applied.
* It can be set to one of the following:
    * HTTP: You must additionally set HTTP URL, HTTP method, and HTTP status code.
    * HTTPS: You must additionally set HTTP URL, HTTP method, and HTTP status code.
    * TCP: The default when not set.

The HTTP URL can be set as follows:

* The setting location is loadbalancer.nhncloud/healthmonitor-http-url under .metadata.annotations.
* Per-listener settings can be applied.
* The setting value must start with /.
* If not set or a value that does not match the rule is entered, it is set to the default value of /.

The HTTP method can be set as follows:

* The setting location is loadbalancer.nhncloud/healthmonitor-http-method under .metadata.annotations.
* Per-listener settings can be applied.
* Currently, only GET is supported. If not set or another value is entered, it will be set to GET, which is the default value.

The HTTP status code can be set as follows:

* The setting location is loadbalancer.nhncloud/healthmonitor-http-expected-code under .metadata.annotations.
* Per-listener settings can be applied.
* You can enter the value in the form of a single value (e.g. 200), a list (e.g. 200,202), or a range (e.g. 200-204).
* If not set or a value that does not match the rule is entered, it is set to the default value of 200.

#### Set the health check interval
You can set the health check interval.

* The setting location is loadbalancer.nhncloud/healthmonitor-delay under .metadata.annotations.
* Per-listener settings can be applied.
* Set the value in seconds.
* Minimum value of 1, maximum value of 5000.
* If not set or a value out of range is entered, it is set to the default value of 60.

#### Set the health check maximum response time
You can set the maximum response time for health checks.

* The setting location is loadbalancer.nhncloud/healthmonitor-timeout under .metadata.annotations.
* Per-listener settings can be applied.
* Set the value in seconds.
* Minimum value of 1, maximum value of 5000.
* This setting must be smaller than the Health check interval setting setting value.
* If not set or a value out of range is entered, it is set to the default value of 30.
* However, if the input value or setting value is greater than the Health check interval setting, it is set to 1/2 of the Health check interval setting setting value.

#### Set the maximum number of retries for a health check
You can set the maximum number of retries for a health check.

* The setting location is loadbalancer.nhncloud/healthmonitor-max-retries under .metadata.annotations.
* Per-listener settings can be applied.
* Minimum value of 1, maximum value of 10.
* If not set or a value out of range is entered, it is set to the default value of 3.


## Ingress Controller
Ingress Controller routes HTTP and HTTPS requests from cluster externals to internal services, in reference of the rules that are defined at ingress object so as to provide SSL/TSL closure and virtual hosting. For more details on Ingress Controller and Ingress, see [Ingress Controller](https://kubernetes.io/docs/concepts/services-networking/ingress-controllers/), [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/).


### Installing NGINX Ingress Controller
NGINX Ingress Controller is one of the most frequently used ingress controllers. For more details, see [NGINX Ingress Controller](https://kubernetes.github.io/ingress-nginx/) and [NGINX Ingress Controller for Kubernetes](https://www.nginx.com/products/nginx-ingress-controller/). For installation of NGINX Ingress Controller, see [Installation Guide](https://kubernetes.github.io/ingress-nginx/deploy/).


### Diverging Service on URI
Ingress controller can diverge services based on URI. The following figure shows the structure of a simple example of service divergence based on URI.

![ingress-01.png](http://static.toastoven.net/prod_infrastructure/container/kubernetes/ingress-01.png)

#### Create Services and Pods
Manifest is created to create services and pods like below: Associate the `tea` pod to `tea-svc`, and the `coffee` pod to `coffee-svc`.

```yaml
# cafe.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: coffee
spec:
  replicas: 3
  selector:
    matchLabels:
      app: coffee
  template:
    metadata:
      labels:
        app: coffee
    spec:
      containers:
      - name: coffee
        image: nginxdemos/nginx-hello:plain-text
        ports:
        - containerPort: 8080
---
apiVersion: v1
kind: Service
metadata:
  name: coffee-svc
spec:
  ports:
  - port: 80
    targetPort: 8080
    protocol: TCP
    name: http
  selector:
    app: coffee
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: tea
spec:
  replicas: 2
  selector:
    matchLabels:
      app: tea
  template:
    metadata:
      labels:
        app: tea
    spec:
      containers:
      - name: tea
        image: nginxdemos/nginx-hello:plain-text
        ports:
        - containerPort: 8080
---
apiVersion: v1
kind: Service
metadata:
  name: tea-svc
  labels:
spec:
  ports:
  - port: 80
    targetPort: 8080
    protocol: TCP
    name: http
  selector:
    app: tea
```

Apply manifest, and see if deployment, service, and pod is created. The pod must be **Running**.

```
$ kubectl apply -f cafe.yaml
deployment.apps/coffee created
service/coffee-svc created
deployment.apps/tea created
service/tea-svc created

# kubectl get deploy,svc,pods
NAME                     READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/coffee   3/3     3            3           27m
deployment.apps/tea      2/2     2            2           27m

NAME                 TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)   AGE
service/coffee-svc   ClusterIP   10.254.171.198   <none>        80/TCP    27m
service/kubernetes   ClusterIP   10.254.0.1       <none>        443/TCP   5h51m
service/tea-svc      ClusterIP   10.254.184.190   <none>        80/TCP    27m

NAME                          READY   STATUS    RESTARTS   AGE
pod/coffee-7c86d7d67c-pr6kw   1/1     Running   0          27m
pod/coffee-7c86d7d67c-sgspn   1/1     Running   0          27m
pod/coffee-7c86d7d67c-tqtd6   1/1     Running   0          27m
pod/tea-5c457db9-fdkxl        1/1     Running   0          27m
pod/tea-5c457db9-z6hl5        1/1     Running   0          27m
```

#### Create Ingress
According to the request path, ingress manifest is created for service connection. A request with `/tea` as endpoint is connected to the `tea-svc` service, while `/coffee` is connected to the `coffee-svc` service.

```yaml
# cafe-ingress-uri.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: cafe-ingress-uri
spec:
  ingressClassName: nginx
  rules:
  - http:
      paths:
      - path: /tea
        pathType: Prefix
        backend:
          service:
            name: tea-svc
            port:
              number: 80
      - path: /coffee
        pathType: Prefix
        backend:
          service:
            name: coffee-svc
            port:
              number: 80
```

In a while after ingress is created, IP must be configured at the **ADDRESS** field.

```
$ kubectl apply -f cafe-ingress-uri.yaml
ingress.networking.k8s.io/cafe-ingress-uri created

$ kubectl get ingress cafe-ingress-uri
NAME               CLASS   HOSTS   ADDRESS          PORTS   AGE
cafe-ingress-uri   nginx   *       123.123.123.44   80      23s
```

#### Send HTTP Requests
Send HTTP request to the IP address set for **ADDRESS** of ingress for an external host, to check if the ingress has been properly set.

Request for `/coffee` as endpoint is sent to the `coffee-svc` service so as the `coffee` pod can respond. From the **Server Name**, you can see that `coffee` pods take turns to respond in the round-robin technique.

```
$ curl 123.123.123.44/coffee
Server address: 10.100.24.21:8080
Server name: coffee-7c86d7d67c-sgspn
Date: 11/Mar/2022:06:28:18 +0000
URI: /coffee
Request ID: 3811d20501dbf948259f4b209c00f2f1

$ curl 123.123.123.44/coffee
Server address: 10.100.24.19:8080
Server name: coffee-7c86d7d67c-tqtd6
Date: 11/Mar/2022:06:28:27 +0000
URI: /coffee
Request ID: ec82f6ab31d622895374df972aed1acd

$ curl 123.123.123.44/coffee
Server address: 10.100.24.20:8080
Server name: coffee-7c86d7d67c-pr6kw
Date: 11/Mar/2022:06:28:31 +0000
URI: /coffee
Request ID: fec4a6111bcc27b9cba52629e9420076
```

Likewise, request for `/tea` as endpoint is delivered to the `tea-svc` service so as the `tea` can respond.

```
$ curl 123.123.123.44/tea
Server address: 10.100.24.23:8080
Server name: tea-5c457db9-fdkxl
Date: 11/Mar/2022:06:28:36 +0000
URI: /tea
Request ID: 11be1b7634a371a26e6bf2d3e72ab8aa
$ curl 123.123.123.44/tea
Server address: 10.100.24.22:8080
Server name: tea-5c457db9-z6hl5
Date: 11/Mar/2022:06:28:37 +0000
URI: /tea
Request ID: 21106246517263d726931e0f85ea2887
```

When a request is sent to undefined URI, the ingress controller sends `404 Not Found` as response.

```
$ curl 123.123.123.44/unknown
<html>
<head><title>404 Not Found</title></head>
<body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx</center>
</body>
</html>
```

#### Delete Resources
Resources for testing can be deleted with used manifest.

```
$ kubectl delete -f cafe-ingress-uri.yaml
ingress.networking.k8s.io "cafe-ingress-uri" deleted

$ kubectl delete -f cafe.yaml
deployment.apps "coffee" deleted
service "coffee-svc" deleted
deployment.apps "tea" deleted
service "tea-svc" deleted
```

### Service Divergence on Host
Ingress controller can diverge services based on the host name. The following figure shows the structure of a simple example of service divergence based on the host name.

![ingress-02.png](http://static.toastoven.net/prod_infrastructure/container/kubernetes/ingress-02.png)

#### Create Services and Pods
Create services and pods by using the same manifest as [URI-based Service Divergence](/Container/NKS/zh/user-guide/#uri).

#### Create Ingress
Write the ingress manifest connecting services based on the host name. Incoming request via the `tea.cafe.example.com` host is connected to the `tea-svc` service, while request via the `coffee.cafe.example.com` host is connected to the `coffee-svc` service.

```yaml
# cafe-ingress-host.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: cafe-ingress-host
spec:
  ingressClassName: nginx
  rules:
  - host: tea.cafe.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: tea-svc
            port:
              number: 80
  - host: coffee.cafe.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: coffee-svc
            port:
              number: 80
```

In a while after ingress is created, IP must be configured at the **ADDRESS** field.

```
$ kubectl apply -f cafe-ingress-host.yaml
ingress.networking.k8s.io/cafe-ingress-host created

$ kubectl get ingress
NAME                CLASS   HOSTS                                          ADDRESS          PORTS   AGE
cafe-ingress-host   nginx   tea.cafe.example.com,coffee.cafe.example.com   123.123.123.44   80      36s
```

#### Send HTTP Requests
HTTP request is sent from external host to IP configured at the ADDRESS of the ingress controller. Nevertheless, such request must be sent by using host name, since service divergence is based on the host name by configuration.

> [Note]
> To test with a random host name, use the --resolve option of curl: enter the --resolve option in the `{Host Name}:{Port Number}:{IP}`format. This means to resolve a request for {Port Number} to be sent to {Host Name} as {IP}.
> You may open up the `/etc/host` file and add `{IP} {Host Name}`.

When a request is sent to the `coffee.cafe.example.com` host, it is delivered to`coffee-svc` so that the `coffee` pod can respond.

```
$ curl --resolve coffee.cafe.example.com:80:123.123.123.44 http://coffee.cafe.example.com/
Server address: 10.100.24.27:8080
Server name: coffee-7c86d7d67c-fqn6n
Date: 11/Mar/2022:06:40:59 +0000
URI: /
Request ID: 1efb60d29891d6d48b5dcd9f5e1ba66d
```

When a request is sent to the `tea.cafe.example.com` host, it is delivered to `tea-svc` so that the `tea` pod can respond.

```
$ curl --resolve tea.cafe.example.com:80:123.123.123.44 http://tea.cafe.example.com/
Server address: 10.100.24.28:8080
Server name: tea-5c457db9-ngrxq
Date: 11/Mar/2022:06:41:39 +0000
URI: /
Request ID: 5a6cc490893636029766b02d2aab9e39
```

When it is requested to an unknown host, the ingress controller sends `404 Not Found` as response.

```
$ curl 123.123.123.44/unknown
<html>
<head><title>404 Not Found</title></head>
<body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx</center>
</body>
</html>
```

## Kubernetes Dashboard
NHN Kubernetes Service (NKS) provides the default web UI dashboard. For more details on Kubernetes Dashboard, see [Web UI (Dashboard)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/).

### Opening Dashboard Services
User Kubernetes has the `kubernetes-dashboard` service object which has been already created to publicly open dashboard.

```
$ kubectl get svc kubernetes-dashboard -n kube-system
NAME                   TYPE        CLUSTER-IP    EXTERNAL-IP   PORT(S)   AGE
kubernetes-dashboard   ClusterIP   10.254.85.2   <none>        443/TCP   6h

$ kubectl describe svc kubernetes-dashboard -n kube-system
Name:              kubernetes-dashboard
Namespace:         kube-system
Labels:            k8s-app=kubernetes-dashboard
Annotations:       <none>
Selector:          k8s-app=kubernetes-dashboard
Type:              ClusterIP
IP Family Policy:  SingleStack
IP Families:       IPv4
IP:                10.254.85.2
IPs:               10.254.85.2
Port:              <unset>  443/TCP
TargetPort:        8443/TCP
Endpoints:         10.100.24.7:8443
Session Affinity:  None
Events:            <none>
```

However, the `kubernetes-dashboard` object belongs to ClusterIP type and is not open out of the cluster. To open up dashboard externally, the service object type must be changed into LoadBalancer, or ingress controller and ingress object must be created.

#### Change into LoadBalancer

Once the type of service object is changed into `LoadBalancer`, NHN Cloud Load Balancer is created out of the cluster, which is associated with load balancer and service object. By querying service object associated with the load balancer, IP of the load balancer is displayed in the **EXTERNAL-IP** field. See [LoadBalancer Service](/Container/NKS/zh/user-guide/#loadbalancer) for the description of service objects of the `LoadBalancer` type. The following figure shows the structure of making dashboard public using the `LoadBalancer` type service.

![dashboard-01.png](http://static.toastoven.net/prod_infrastructure/container/kubernetes/dashboard-01.png)

Change the type of the `kubernetes-dashboard` service object to `LoadBalancer`, like below:

```
$ kubectl -n kube-system patch svc/kubernetes-dashboard -p '{"spec":{"type":"LoadBalancer"}}'
service/kubernetes-dashboard patched
```

After the type of service object `kubernetes-dashboard` is changed to `LoadBalancer`, you can check load balancer IP from the **EXTERNAL-IP** field.

```
$ kubectl get svc -n kube-system
NAME                   TYPE           CLUSTER-IP      EXTERNAL-IP      PORT(S)                  AGE
...
kubernetes-dashboard   LoadBalancer   10.254.95.176   123.123.123.81   443:30963/TCP            2d23h
```

> [Note]
> You can view the created load balancer on the **Network > Load Balancer** page.
> Load balancer IP is a floating IP allowing external access. You can check it on the **Network > Floating IP** page.

If you access `https://{EXTERNAL-IP}` in a web browser, the Kubernetes dashboard page is loaded. See [Dashboard Access Token](/Container/NKS/zh/user-guide/#dashboard-access-token) for the token required for login.

> [Note]
> Since Kubernetes dashboard is based on a private certificate that is automatically created, the page may be displayed as unsafe, depending on the web browser or security setting.

#### Open Services with Ingress

Ingress refers to the network object providing routing to access many services within a cluster. The setting of an ingress object runs by ingress controller. The `kubernetes-dashboard` service object can go public through ingress. See [Ingress Controller](/Container/NKS/zh/user-guide/#ingress-controller) regarding description on ingress and ingress controller. The following figure shows the structure of making dashboard public through ingress.

![dashboard-02.png](http://static.toastoven.net/prod_infrastructure/container/kubernetes/dashboard-02.png)

Install `NGINX Ingress Controller` by referring to [Install NGINX Ingress Controller](/Container/NKS/zh/user-guide/#nginx-ingress-controller) and write the manifest for creating an ingress object as follows.

```yaml
# kubernetes-dashboard-ingress-tls-passthrough.yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: k8s-dashboard-ingress
  namespace: kube-system
  annotations:
    ingress.kubernetes.io/ssl-passthrough: "true"
    kubernetes.io/ingress.allow-http: "false"
    nginx.ingress.kubernetes.io/backend-protocol: HTTPS
    nginx.ingress.kubernetes.io/proxy-body-size: 100M
    nginx.ingress.kubernetes.io/rewrite-target: /
    nginx.org/ssl-backend: kubernetes-dashboard
spec:
  ingressClassName: nginx
  rules:
  - http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: kubernetes-dashboard
            port:
              number: 443
  tls:
  - secretName: kubernetes-dashboard-certs
```

Apply the manifest to create an ingress and check the **ADDRESS** field of the ingress object.

```
$ kubectl apply -f kubernetes-dashboard-ingress-tls-passthrough.yaml
ingress.networking.k8s.io/k8s-dashboard-ingress created

$ kubectl get ingress -n kube-system
NAME                    CLASS   HOSTS   ADDRESS          PORTS     AGE
k8s-dashboard-ingress   nginx   *       123.123.123.44   80, 443   34s
```

If you access `https://{ADDRESS}` in a web browser, the Kubernetes dashboard page is loaded. See [Dashboard Access Token](/Container/NKS/zh/user-guide/#dashboard-access-token) for the token required for login.

### Dashboard Access Token
A token is required to log in to the Kubernetes dashboard. You can get the token with the following command:

```
# SECRET_NAME=$(kubectl -n kube-system get secrets | grep "kubernetes-dashboard-token" | cut -f1 -d ' ')

$ kubectl describe secret $SECRET_NAME -n kube-system | grep -E '^token' | cut -f2 -d':' | tr -d " "
eyJhbGc...-QmXA
```

Enter the printed token in the token input window on the browser, and you can log in as a user that has been granted the cluster admin privileges.


## Persistent Volume
Persistent Volume or PV is a Kubernetes resource representing physical storage volume. One PV is attached to one NHN Cloud Block Storage. For more details, see [Persistent Volume](https://kubernetes.io/docs/concepts/storage/persistent-volumes/).

Persistent Volume Claims, or PVC is required to attach PV to pods. PVC defines necessary volume requirements, including volume and read/write modes.

With PV and PVC, user can define the attributes of a volume of choice, while the system seperates the use of resources from management by assigning volume resources for each user requirement.

### Life Cycle of PV/PVC
PV and PVC support the four-phase life cycle.

* Provisioning
Using [storage classes](https://kubernetes.io/docs/concepts/storage/storage-classes/), users can manually secure a volume and create a PV (static provisioning) or dynamically create a PV (dynamic provisioning).

* Binding
Bind PV to PVC 1:1. With dynamic provisioning, binding is also automatically executed along with PV provisioning.

* Using
Mount PV to a pod to make it enabled.

* Reclaiming
Volume is reclaimed after it is used up, in three methods: Delete, Retain, or Recycle.

| Method | Description |
| --- | --- |
| Delete | PV is deleted along with its attached volumes. |
| Retain | PV is deleted but its attached volumes are not: volumes can be deleted or reused by user. |
| Recycle | PV is deleted and its attached volumes are made to be reused without being deleted. This method has been deprecated. |

### Storage Class (StorageClass)
A storage class must be defined before provisioning. Storage classes provide a way to classify storages by certain characteristics. You can set the information such as media type and availability zone by including information about the storage provider (provisioner). 

#### Storage Provider (provisioner)
Set the provider information of storage. Depending on the Kubernetes version, the supported storage provider information is as follows:

* v1.19.13 or earlier: The provisioner field must be set to `kubernetes.io/cinder`.
* v1.20.12 or later: You can use the provisioner field by setting it to `cinder.csi.openstack.org`.

#### Parameters (parameter)
The storage class allows you to set the following parameters:

* Storage type (type): Enter the type of storage. (If not entered, General HDD is set.)
    * **General HDD**: The storage type is set to HDD.
    * **General SSD**: The storage type is set to SSD.
* Availability zone (availability): Set the availability zone. (If not entered, it will be set randomly.)
    * Pangyo Region: **kr-pub-a** or **kr-pub-b**
    * Pyeongchon region: **kr2-pub-a** or **kr2-pub-b**

#### Volume Binding Mode (VolumeBindingMode)
A volume binding mode controls the time when volume binding and dynamic provisioning start. This setting is configurable only if the storage provider is cinder.csi.openstack.org. 

* **Immediate**: Volume binding and dynamic provisioning start as soon as a persistent volume claim is created. When the persistent volume claim is created, there is no prior knowledge of the pods to which the volume will be attached. Therefore, if the availability zone of the volume and the availability zone of the node on which the pod will be scheduled are different, the pod will not work properly. 
* **WaitForFirstConsumer**: Volume binding and dynamic provisioning are not performed when a persistent volume claim is created. When this persistent volume claim is attached to a pod for the first time, volume binding and dynamic provisioning are performed based on the availability zone information of the node on which the pod is scheduled. Therefore, there is no case where the pod does not work properly because the availability zone of the volume and the availability zone of the instance are different, such as in Immediate mode.

#### Example 1
The storage class manifest below can be used for Kubernetes clusters using v1.19.13 or earlier. You can use parameters to specify the availability zone and volume type.

```yaml
# storage_class.yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: sc-ssd
provisioner: kubernetes.io/cinder
parameters:
  type: General SSD
  availability: kr-pub-a
```

Create the storage class and check that it has been created.

```
$ kubectl apply -f storage_class.yaml
storageclass.storage.k8s.io/sc-ssd created

$ kubectl get sc
NAME     PROVISIONER            RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
sc-ssd   kubernetes.io/cinder   Delete          Immediate           false                  3s
```

#### Example 2
The storage class manifest below can be used for Kubernetes clusters using v1.20.12 or later. Set the volume binding mode to WaitForFirstConsumer to initiate volume binding and dynamic provisioning when a persistent volume claim is attached to a pod.

```yaml
# storage_class_csi.yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: csi-storageclass
provisioner: cinder.csi.openstack.org
volumeBindingMode: WaitForFirstConsumer
```

Create the storage class and check that it has been created.

```
$ kubectl apply -f storage_class_csi.yaml
storageclass.storage.k8s.io/csi-storageclass created

$ kubectl get sc
NAME               PROVISIONER                RECLAIMPOLICY   VOLUMEBINDINGMODE      ALLOWVOLUMEEXPANSION   AGE
csi-storageclass   cinder.csi.openstack.org   Delete          WaitForFirstConsumer   false                  7s
```


### Static Provisioning

Static provisioning requires the user to prepare a block storage manually. On the **Storage > Block Storage** service page of the NHN Cloud web console, click the **Create Block Storage** button to create a block storage to attach to the PV. See [Create Block Storage](/Storage/Block%20Storage/zh/console-guide/#create-block-storage) in the Block Storage guide.

To create a PV, you need the ID of the block storage. On the **Storage > Block Storage** service page, select the block storage you want to use from the block storage list. You can find the ID under the block storage name section in the **Information** tab at the bottom.

Write a manifest for the PV to be attached to the block storage. Enter the storage class name in **spec.storageClassName**. To use NHN Cloud Block Storage, **spec.accessModes** must be set to `ReadWriteOnce`. **spec.presistentVolumeReclaimPolicy** can be set to `Delete` or `Retain`.

> [Caution]
> You must set a storage class in which the storage provider suitable for your Kubernetes version has been defined.

```yaml
# pv-static.yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-static-001
spec:
  capacity:
    storage: 10Gi
  volumeMode: Filesystem
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Delete
  storageClassName: sc-default
  cinder:
    fsType: "ext3"
    volumeID: "e6f95191-d58b-40c3-a191-9984ce7532e5"
```

Create the PV and check that it has been created.

```
$ kubectl apply -f pv-static.yaml
persistentvolume/pv-static-001 created

$ kubectl get pv -o wide
NAME            CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS   REASON   AGE   VOLUMEMODE
pv-static-001   10Gi       RWO            Delete           Available           sc-default              7s    Filesystem
```

Write a PVC manifest to use the created PV. The PV name must be specified in **spec.volumeName**. Set other items the same as PV manifest.

```yaml
# pvc-static.yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-static
  namespace: default
spec:
  volumeName: pv-static-001
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
  storageClassName: sc-default
```

Create the PVC and check that it has been created.

```
$ kubectl apply -f pvc-static.yaml
persistentvolumeclaim/pvc-static created

$ kubectl get pvc -o wide
NAME         STATUS   VOLUME          CAPACITY   ACCESS MODES   STORAGECLASS   AGE   VOLUMEMODE
pvc-static   Bound    pv-static-001   10Gi       RWO            sc-default     7s    Filesystem
```

After the PVC is created, query PV status, and you can find PVC name specified for **CLAIM** and **STATUS** changed into `Bound`.

```
$ kubectl get pv -o wide
NAME            CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                STORAGECLASS   REASON   AGE   VOLUMEMODE
pv-static-001   10Gi       RWO            Delete           Bound    default/pvc-static   sc-default              79s   Filesystem
```


### Dynamic Provisioning

With Dynamic Provisioning, block storage is automatically created in reference of attributes defined at storage class. To use Dynamic Provisioning, do not set Volume Binding Mode of storage class or set it to **Immediate**.

```yaml
# storage_class_csi_dynamic.yaml
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: csi-storageclass-dynamic
provisioner: cinder.csi.openstack.org
volumeBindingMode: Immediate
```

There is no need to create PV for dynamic provisioning; therefore, PVC manifest does not require the setting of **spec.volumeName**.


```yaml
# pvc-dynamic.yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pvc-dynamic
  namespace: default
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
  storageClassName: csi-storageclass-dynamic
```

If you do not set the volume binding mode or set it to **Immediate** and create a PVC, the PV will be created automatically. At the same time, block storage attached to the PV is also automatically created, and you can check it from the list of block storages on the **Storage > Block Storage** page of the NHN Cloud web console.

```
$ kubectl apply -f pvc-dynamic.yaml
persistentvolumeclaim/pvc-dynamic created

$ kubectl get sc,pv,pvc
NAME                                                   PROVISIONER                RECLAIMPOLICY   VOLUMEBINDINGMODE   ALLOWVOLUMEEXPANSION   AGE
storageclass.storage.k8s.io/csi-storageclass-dynamic   cinder.csi.openstack.org   Delete          Immediate           false                  50s

NAME                                                        CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM                 STORAGECLASS               REASON   AGE
persistentvolume/pvc-1056949c-bc67-45cc-abaa-1d1bd9e51467   10Gi       RWO            Delete           Bound    default/pvc-dynamic   csi-storageclass-dynamic            5s

NAME                                STATUS   VOLUME                                     CAPACITY   ACCESS MODES   STORAGECLASS               AGE
persistentvolumeclaim/pvc-dynamic   Bound    pvc-1056949c-bc67-45cc-abaa-1d1bd9e51467   10Gi       RWO            csi-storageclass-dynamic   9s
```

> [Caution]
> A block storage created by dynamic provisioning cannot be deleted from the web console. It is not automatically deleted along with a cluster being deleted. Therefore, before a cluster is deleted, all PVCs must be deleted first; otherwise, you may be charged for PVC usage. The reclaimPolicy of PV created by dynamic provisioning is set to `Delete` by default, so deleting only the PVC will also delete the PV and block storage.


### Mounting PVC to Pods

To mount PVC to a pod, mount information must be defined at the pod manifest. Enter the PVC name to use in `spec.volumes.persistenVolumeClaim.claimName`; enter paths to mount in `spec.containers.volumeMounts.mountPath`.

In the following example, a PVC created with static provisioning is mounted to `/usr/share/nginx/html` of the pod.

```yaml
# pod-pvc.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-with-static-pv
spec:
  containers:
    - name: web
      image: nginx
      ports:
        - name: web
          containerPort: 80
          hostPort: 8082
          protocol: TCP
      volumeMounts:
        - name: html-volume
          mountPath: "/usr/share/nginx/html"
  volumes:
    - name: html-volume
      persistentVolumeClaim:
        claimName: pvc-static
```

Create the pod and see if the block storage has been mounted.

```
$ kubectl apply -f pod-static-pvc.yaml
pod/nginx-with-static-pv created

$ kubectl get pods
NAME                   READY   STATUS    RESTARTS   AGE
nginx-with-static-pv   1/1     Running   0          50s

$ kubectl exec -ti nginx-with-static-pv -- df -h
Filesystem      Size  Used Avail Use% Mounted on
...
/dev/vdc        9.8G   23M  9.7G   1% /usr/share/nginx/html
...
```

You can also check block storage attachment information in the **Storage > Block Storage** service page of the NHN Cloud web console.
