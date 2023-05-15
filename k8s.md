## Fundamentals of Kubernetes Deployment

[Link to course](https://www.coursera.org/learn/kubernetes-deployment)

<a name="link-top"></a>

---

### Table of Contents

<ol>
  <li>
    <a href="#kubernetes-overview">Module 1</a>
      <ul>
        <li>
          <a href="#kubernetes-overview">1.1 Kubernetes Overview</a>
        </li>
        <li>
          <a href="#kubernetes-architecture">1.2 Kubernetes Architecture</a>
        </li>
      </ul>
  </li>
  <li>
    <a href="#kubernetes-components-and-installation-options">Module 2</a>
      <ul>
        <li>
          <a href="#kubernetes-components-and-installation-options">2.1 Kubernetes Components and Installation Options</a>
        </li>
        <li>
          <a href="#installing-minikube">2.2 Installing Minikube</a>
        </li>
      </ul>
  </li>
</ol>

---

#### Module 1.1

#### Kubernetes Overview

#### Q1. Kubernetes began as a project at which company?

1. [ ] Yahoo
2. [ ] Facebook
3. [x] Google
4. [ ] Amazon

#### Q2. Monoliths are expensive and difficult to manage. What has made monoliths obsolete?

1. [ ] DevOps
2. [ ] Legacy Hardware
3. [ ] Main Frames
4. [x] Microservices

#### Explanation:

Microservices architecture has made monoliths obsolete. With the microservices approach, an application is broken down
into smaller, independent
services that can be developed, deployed, and scaled independently of each other. This makes it easier to manage the
application, update and deploy
new features, and scale as needed.

Monolithic architectures can still be used in some cases, but microservices have become popular due to their flexibility
and ability to support
continuous delivery and deployment.

#### Q3. True or False: Containers consist of applications and dependencies

1. [x] True
2. [ ] False

#### Explanation:

Containers are a way to package and run applications with their dependencies in a portable and consistent way. This
means that a container includes
not only the application code but also all of its dependencies, such as libraries, binaries, and configuration files. By
packaging everything together
in a container, the application can be run reliably and consistently across different environments, without any
conflicts or dependencies issues.

#### Q4. True or False: Multiple containers cannot run on the same operating system and share the same hardware.

1. [ ] True
2. [x] False

#### Explanation:

Multiple containers can run on the same operating system and share the same hardware.

Containerization technology is designed to allow multiple containers to run on a single host operating system. Each
container is isolated from the
others, but they share the same kernel and other system resources, such as CPU, memory, and disk I/O. This allows for
efficient use of hardware
resources and makes it possible to run many containers on a single machine.

#### Q5. Container Orchestration supports all but which of the following?

1. [ ] Real time scalability
2. [x] Level 3 support
3. [ ] On-line updates, recovery and rollbacks without downtime.
4. [ ] Fault-Tolerance: business continuity

#### Explanation:

Level 3 support typically refers to a specific level of technical support that a vendor provides to customers (not k8s
feature).

#### Q6. True or False: Kubernetes can be installed on “bare metal”, virtual machines, private or public Cloud.

1. [x] True
2. [ ] False

#### Explanation:

Kubernetes can be installed on a variety of infrastructure platforms, including "bare metal" servers, virtual machines,
private clouds, and
public clouds. This is one of the key benefits of Kubernetes - it is highly portable and can run on any infrastructure
platform, allowing
organizations to deploy and manage containerized applications in a consistent way across different environments.

#### Q7. The Kubernetes product is managed by which organization?

1. [ ] Google
2. [ ] Amazon Web Services
3. [x] Cloud Native Computing Foundation (CNCF)
4. [ ] IBM

#### Q8. Which of the following features supporting Container Orchestration does Kubernetes NOT offer?

1. [ ] Self-healing
2. [x] Application builds
3. [ ] Container runtimes
4. [ ] Service discovery and load balancing.

#### Explanation:

Kubernetes does not provide built-in application build capabilities. While Kubernetes can manage and deploy
containerized applications, it does not handle the actual process of building the container images. Instead,
organizations typically use separate tools or services to build the container
images, which can then be deployed to Kubernetes clusters.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 1.2

#### Kubernetes Architecture

#### Q1. The two types of Kubernetes nodes are?

1. [x] Master and Worker
2. [ ] On premises and remote
3. [ ] Right and left
4. [ ] Base and runner

#### Explanation:

The two types of Kubernetes nodes are the Master node and the Worker node. The Master node is responsible for managing
the overall state of the cluster, while the Worker nodes are responsible for running the actual application workloads.

* The Master node controls and coordinates all the activities in the cluster, such as scheduling the workloads to run on
  the Worker nodes, monitoring the health of the nodes and the workloads, and scaling the resources up or down as
  needed.
* The Worker nodes, on the other hand, are the actual compute nodes that run the application workloads and provide the
  necessary resources such as
  CPU, memory, and storage.

#### Q2. True or False: The Worker Node does not host the container runtime.

1. [ ] True
2. [x] False

#### Explanation:

False.

The Worker Node in a Kubernetes cluster is responsible for running the application workloads and providing the necessary
resources such as CPU, memory, and storage. One of the key components required to run containers on a Worker Node is a
container runtime.

Therefore, the Worker Node must host the container runtime. The container runtime is responsible for pulling the
container images from a container registry, creating the container instances, and managing the lifecycle of the
containers.

#### Q3. True or False: The state of the Kubernetes cluster is stored in the etcd

1. [x] True
2. [ ] False

#### Explanation:

True.

The state of a Kubernetes cluster, including information about the nodes, pods, services, and other resources, is stored
in etcd, which is a distributed key-value store.

Etcd is a highly available and consistent datastore that can store and retrieve configuration data in real-time, making
it an ideal choice for storing the state of a Kubernetes cluster.

The Kubernetes control plane components, including the API server, controller manager, and scheduler, interact with etcd
to read and write cluster state information.

![k8s-control-plane.png](src%2Fkubernetes%2Fk8s-control-plane.png)

#### Q4. A Pod consists of one or more ________ .

1. [ ] Kublets
2. [x] Containers
3. [ ] User Interfaces
4. [ ] Schedulers

#### Explanation:

A Pod can contain one or more containers, and they share the same network namespace and can communicate with each other
via localhost.

#### Q5. The worker node has all the following components except:

1. [ ] Kubelet
2. [ ] Pod
3. [ ] Kube-Proxy
4. [x] Keypad

#### Explanation:

The worker node in Kubernetes has three main components which include:

* **Kubelet**: A service that runs on each node and communicates with the Kubernetes control plane. Kubelet is
  responsible for starting, stopping, and maintaining application containers within a pod.
* **Pod**: The smallest deployable unit in Kubernetes that represents a single instance of a running process in a
  cluster.
* **Kube-proxy**: A network proxy that runs on each node and provides networking services for pods.

![k8s-working-node.png](src%2Fkubernetes%2Fk8s-working-node.png)

#### Q6. All container runtimes are supported on Kubernetes except _______ .

1. [ ] rklet
2. [ ] CRI-O
3. [x] Podlet
4. [ ] Docker

#### Explanation:

"Podlet" is not a container runtime and is not supported on Kubernetes. The other options, including Docker and CRI-O,
are both container runtimes that are supported on Kubernetes.

The Kubernetes runtime interface (CRI) defines an interface between Kubernetes and container runtimes.

* **rktlet** is a Kubernetes Container Runtime Interface implementation using rkt as the main container runtime
* **CRI-O** is a lightweight, Open Container Initiative (OCI)-compliant container runtime that supports the CRI
  interface.
* **Docker** is also a container runtime that supports the CRI interface, and it was the original runtime used by
  Kubernetes.

#### Q7. Which runtime is a pod-native Container Runtime?

1. [x] rklet
2. [ ] CRI-O
3. [ ] Docker

#### Q8. Which of the following is a service that communicates with the Master Node and containers?

1. [x] kubelet
2. [ ] Pod
3. [ ] Dashboard

#### Explanation:

Kubelet is a service that runs on each node and communicates with the Kubernetes control plane. Kubelet is
responsible for starting, stopping, and maintaining application containers within a pod.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

#### Discussion Prompt: The Kubernetes Nodes and Pods

#### Discuss the Kubernetes Nodes, Pods, and each node's components such as the scheduler and etcd. How does the worker node communicate with the master node? Which nodes run container runtimes?

The two types of Kubernetes nodes are the Master node and the Worker node.

The **Master node** controls and coordinates all the activities in the cluster, such as scheduling the workloads to run
on the Worker nodes, monitoring the health of the nodes and the workloads, and scaling the resources up or down as
needed.

![k8s-control-plane.png](src%2Fkubernetes%2Fk8s-control-plane.png)

The master node runs several Kubernetes components that handle the core functionality of the cluster, including:

1. The **API server** provides a central point of contact for the Kubernetes control plane and serves as the interface
   for managing the cluster's state and resources. It processes REST API requests, validates them, and updates the etcd
   datastore with the desired state of the cluster.
2. **Etcd** is a distributed key-value store that stores the state of the Kubernetes cluster, including information
   about the nodes, pods, services, and other resources.
3. The **Scheduler** is responsible for scheduling pods to run on worker nodes based on resource availability and
   scheduling constraints.
4. The **Controller manager** is responsible for managing various controllers that watch the state of the cluster and
   take actions to ensure that the desired state is achieved and maintained.

---

The **Worker nodes**, on the other hand, are the actual compute nodes that run the application workloads and provide the
necessary resources such as CPU, memory, and storage.

![k8s-working-node.png](src%2Fkubernetes%2Fk8s-working-node.png)

The worker node in Kubernetes has three main components which include:

* **Kubelet**: A service that runs on each node and communicates with the Kubernetes control plane. Kubelet is
  responsible for starting, stopping, and maintaining application containers within a pod.
* **Pod**: The smallest deployable unit in Kubernetes that represents a single instance of a running process in a
  cluster.
* **Kube-proxy**: A network proxy that runs on each node and provides networking services for pods.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 2.1

#### Kubernetes Components and Installation Options

#### Q1. Kubernetes can be installed on all operating systems except ______ .

1. [ ] Ubuntu
2. [x] Android
3. [ ] Windows
4. [ ] Redhat

#### Explanation:

Kubernetes can be installed on Ubuntu, Redhat, and Windows operating systems. However, it cannot be installed on Android
as it is a mobile operating system and not suitable for running complex containerized applications.

#### Q2. True or False: kops is a tool for installing Kubernetes on Amazon Web Services (AWS)

1. [x] True
2. [ ] False

#### Explanation:

True.

Kops is a popular open-source tool that is used for installing, operating, and managing production-grade Kubernetes
clusters on Amazon Web Services (AWS). It helps simplify the process of setting up and managing a Kubernetes cluster on
AWS, providing users with features such as automatic scaling, self-healing, and high availability.

Example of the command for creating a Kubernetes cluster:

```
kops create cluster \
--node-count 3 \
--node-size t2.micro \
--zones us-west-2a,us-west-2b \
--name my-kubernetes-cluster.example.com \
--yes
```

This command creates a cluster with three worker nodes of size t2.micro in two availability zones (us-west-2a and
us-west-2b) in the us-west-2 region.

#### Q3. The command kubectl describe node <insert-node-name-here>, returns what?

1. [ ] Help documentation
2. [ ] Deployment status
3. [ ] Pod status
4. [x] Node addresses, status and details

#### Explanation:

The command `kubectl describe node <insert-node-name-here>` returns the node addresses, status, and details of the node.

This includes information such as the node name, node IP address, node labels and annotations, the amount of CPU and
memory available on the node, and the status of the node's kubelet and container runtime. It also includes any taints or
toleration's that have been applied to the node, as well as any attached storage devices.

Overall, the command provides a detailed overview of the specified node in the Kubernetes cluster.

An example output of the kubectl describe node `<insert-node-name-here>` command:

```
Name:               ip-10-0-1-123.ec2.internal
Roles:              <none>
Labels:             beta.kubernetes.io/arch=amd64
beta.kubernetes.io/instance-type=t2.micro
beta.kubernetes.io/os=linux
kubernetes.io/arch=amd64
kubernetes.io/hostname=ip-10-0-1-123.ec2.internal
kubernetes.io/os=linux
Annotations:        node.alpha.kubernetes.io/ttl=0
volumes.kubernetes.io/controller-managed-attach-detach=true
...
Status:
Capacity:
cpu:                2
ephemeral-storage:  20484756Ki
hugepages-1Gi:      0
hugepages-2Mi:      0
memory:             2017408Ki
pods:               110
Allocatable:
cpu:                1944m
ephemeral-storage:  18808761968
hugepages-1Gi:      0
hugepages-2Mi:      0
memory:             1775288Ki
pods:               110
...
Addresses:
InternalIP:   10.0.1.123
Hostname:     ip-10-0-1-123.ec2.internal
...
Conditions:
Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
OutOfDisk        False   Fri, 03 Sep 2021 16:31:43 +0000   Fri, 03 Sep 2021 16:30:33 +0000   KubeletHasSufficientDisk     kubelet has sufficient disk space available
MemoryPressure   False   Fri, 03 Sep 2021 16:31:43 +0000   Fri, 03 Sep 2021 16:30:33 +0000   KubeletHasSufficientMemory   kubelet has sufficient memory available
DiskPressure     False   Fri, 03 Sep 2021 16:31:43 +0000   Fri, 03 Sep 2021 16:30:33 +0000   KubeletHasNoDiskPressure     kubelet has no disk pressure
...
```

#### Q4. True or False: All communication between the cluster to the master node are accessed through the apiserver.

1. [x] True
2. [ ] False

#### Explanation:

True.

All communication between the cluster and the master node is accessed through the apiserver.

![k8s-cluster.png](src%2Fkubernetes%2Fk8s-cluster.png)

The Kubernetes API server is the central control point for all communication in a Kubernetes cluster, serving as the
front-end for the Kubernetes API and acting as the gateway for all administrative actions and queries against the
cluster.

#### Q5. True or false? It's important to check Kubernetes documentation for the latest installment requirements.

1. [x] True
2. [ ] False

#### Explanation:

True.

Keeping up-to-date with the latest installation requirements will help ensure that your Kubernetes cluster is stable and
running optimally.

The requirements may change with different versions of Kubernetes and the documentation will provide information about
system requirements, dependencies, and other prerequisites necessary to install and run Kubernetes successfully.

#### Q6. How many primary communication paths are there from the Master (apiserver) to the cluster?

1. [x] 2
2. [ ] 3
3. [ ] 4

#### Explanation:

There are two primary communication paths from the Master (apiserver) to the cluster:

**Communication with the etcd datastore**:

The apiserver communicates with etcd to store and retrieve cluster state information, such as information about nodes,
pods, services, and other Kubernetes objects. This communication path is essential for managing the cluster's
configuration and state.

**Communication with the kubelet agents on worker nodes**:

The apiserver communicates with the kubelet agents on worker nodes to monitor the state of the nodes and the pods
running on them, and to schedule and manage pod deployments. This communication path enables the apiserver to manage the
runtime state of the cluster.

#### Q7. Connections from apiserver to kubelet are used for all the following except:

1. [x] adding conditions for running pods
2. [ ] attaching to running pods
3. [ ] fetching logs for pods
4. [ ] providing kubelet's port-forwarding functionality

#### Explanation:

Connections from the API server to kubelet are used for the following purposes:

1. **Attaching to running pods**: The API server can attach to a running pod's network namespace to facilitate
   operations like port forwarding, executing commands, or attaching a terminal to a pod.
2. **Fetching logs for pods**: The API server can request log information from the kubelet for a specific pod. This
   allows users to retrieve the logs of their pods through the Kubernetes API.
3. **Providing kubelet's port-forwarding functionality**: The API server can proxy port-forwarding requests from clients
   to the kubelet. This enables users to access services running inside pods via a local port on their machines.

However, "adding conditions for running pods" is not a function performed by the connections from the API server to
kubelet.

#### Q8. True or false? Kubernetes can NOT be built from scratch.

1. [ ] True
2. [x] False

#### Explanation:

False.

Kubernetes can be built from scratch.

Kubernetes is an open-source project, and its source code is available on GitHub. Developers and users can contribute to
the Kubernetes codebase and build their own custom Kubernetes distributions from the source code. The Kubernetes
community provides extensive documentation on how to build and contribute to the project, including instructions on how
to build a custom Kubernetes cluster.

#### Q9. The ________ is a Kubernetes master component that manages various aspects of nodes.

1. [x] node controller
2. [ ] Heartbeat
3. [ ] node topology

#### Explanation:

The Node Controller is a Kubernetes master component that manages various aspects of nodes.

The Node Controller is responsible for monitoring the status of nodes in the cluster, including detecting when a node
becomes unreachable or is shut down, and for taking corrective actions such as rescheduling pods running on the failed
node to other nodes in the cluster.

The Node Controller also ensures that the desired number of replicas of each pod is running on the cluster at all times.

<p align="center"><strong>The difference between Node Controller and the Control Manager?</strong></p>

The Node Controller and the Control Manager are both components of the Kubernetes control plane, but they serve
different purposes and have distinct responsibilities.

1. Node Controller:
   The Node Controller, also known as the Node Manager, is a component in the Kubernetes control plane responsible for
   managing individual nodes in the cluster. Its main tasks include:

- Monitoring the state and health of nodes, detecting failures, and identifying when nodes become unreachable.
- Taking necessary actions to maintain the desired state of nodes, such as marking them as unhealthy, evicting pods, or
  rescheduling pods onto other available nodes.
- Collaborating with other components like the kubelet on each node to ensure proper node management.

The Node Controller ensures the availability and proper functioning of individual nodes within the cluster.

2. Controller Manager:
   The Controller Manager is a crucial component of the Kubernetes control plane that oversees several controllers
   responsible for different aspects of cluster management. It includes controllers such as:

- **Replication Controller/ReplicaSet Controller**: Ensures the desired number of pod replicas is running and handles
  scaling and self-healing.
- **Deployment Controller**: Handles rolling updates and manages the lifecycle of deployments.
- **StatefulSet Controller**: Manages stateful applications by maintaining stable network identities and ordered
  scaling.
- **DaemonSet Controller**: Ensures that a copy of a pod runs on each node in the cluster.
- **Job Controller/CronJob Controller**: Manages batch processing and scheduled jobs.
- **Namespace Controller**: Handles the creation, deletion, and lifecycle of namespaces within the cluster.

The Controller Manager continuously monitors the cluster state and ensures that the desired state, defined through the
Kubernetes API, is maintained by the respective controllers.

In summary, the Node Controller focuses on managing individual nodes, while the Controller Manager oversees multiple
controllers responsible for various aspects of cluster management, such as replication, deployment, and job scheduling.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

