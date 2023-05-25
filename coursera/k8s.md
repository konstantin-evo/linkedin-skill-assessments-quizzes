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
  <li>
    <a href="#kubernetes-hosted-configurations">Module 3</a>
      <ul>
        <li>
          <a href="#kubernetes-hosted-configurations">3.1 Kubernetes Hosted Configurations</a>
        </li>
        <li>
          <a href="#hosted-deployments-scaling-updates-and-rollbacks">3.2 Hosted Deployments, Scaling, Updates and Rollbacks</a>
        </li>
      </ul>
  </li>
  <li>
    <a href="#kublet-proxy-replicasets-daemonset-and-statefulsets">Module 4</a>
      <ul>
        <li>
          <a href="#kublet-proxy-replicasets-daemonset-and-statefulsets">4.1 Kublet, Kube Proxy, Replicasets, Daemonset and StatefulSets</a>
        </li>
        <li>
          <a href="#module-4-2">4.2 PV, PVC, CSI and Authentication and Authorization</a>
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

![k8s-control-plane.png](..%2Fsrc%2Fkubernetes%2Fk8s-control-plane.png)

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

![k8s-working-node.png](..%2Fsrc%2Fkubernetes%2Fk8s-working-node.png)

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

![k8s-control-plane.png](..%2Fsrc%2Fkubernetes%2Fk8s-control-plane.png)

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

![k8s-working-node.png](..%2Fsrc%2Fkubernetes%2Fk8s-working-node.png)

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

![k8s-cluster.png](..%2Fsrc%2Fkubernetes%2Fk8s-cluster.png)

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

---

#### Module 2.2

#### Installing Minikube

#### Q1. Which is the command line subcommand for accessing Kubernetes?

1. [ ] Hypervisor
2. [x] kubectl
3. [ ] AWS
4. [ ] Minikube

#### Explanation:

kubectl is the command-line interface (CLI) tool for interacting with Kubernetes clusters.

It allows you to perform various operations such as deploying and managing applications, inspecting cluster resources,
scaling deployments, and more.

#### Q2. How is minikube started

1. [x] minikube start
2. [ ] minikube.exe
3. [ ] kubectl --start
4. [ ] minikube run

#### Explanation:

To start Minikube, you would typically open your command line or terminal and enter the following command:

```
minikube start
```

This command initializes and starts a Minikube cluster on your local machine. It sets up a single-node Kubernetes
cluster that you can use for local development and testing. Minikube automatically provisions a virtual machine (using a
hypervisor such as VirtualBox, Hyper-V, or KVM) and configures the necessary Kubernetes components to create the
cluster.

#### Q3. The Kubernetes cluster cannot be accessed using?

1. [x] The Kubernetes Office client
2. [ ] The web user interface
3. [ ] Programmatic and script-based API calls or CLI API calls.
4. [ ] The command line interface (CLI)

#### Explanation:

The Kubernetes Office client is not a standard tool or component used to access or interact with Kubernetes clusters.
There is no such widely recognized client called "Kubernetes Office." Therefore, option 1, "The Kubernetes Office
client," is the correct answer.

#### Q4. Command kubectl proxy allows for what?

1. [ ] Starts pods
2. [ ] Get the updated version
3. [x] A proxy server to run
4. [ ] View the API calls

#### Explanation:

The` kubectl proxy` command allows you to create a proxy server between your local machine and a Kubernetes API server.
By running kubectl proxy, you can access the Kubernetes API server locally and view API calls made to the cluster.

When the proxy server is running, you can use tools like curl or web browsers to send API requests to the Kubernetes
cluster. The proxy handles the authentication and forwards the requests to the appropriate API endpoints on your behalf.
It also provides a way to view the API responses and monitor the traffic between your local machine and the cluster.

By accessing the proxy server, you can inspect the API calls being made, observe the responses, and gain insights into
the cluster's behavior and state. This can be useful for debugging, troubleshooting, and understanding how your
applications interact with the Kubernetes API.

#### Q5. True or False: http://localhost:8001/healthz returns the cluster health status

1. [x] True
2. [ ] False

#### Explanation:

Accessing the endpoint http://localhost:8001/healthz typically returns the health status of the Kubernetes cluster's API
server. This endpoint is commonly used to check the availability and health of the API server.

#### Q6. Which of the following is a method for installing a virtualized version of Kubernetes?

1. [ ] kops
2. [ ] kubespray
3. [ ] kubelet
4. [x] minikube

#### Explanation:

Minikube is a method for installing a virtualized version of Kubernetes. It allows you to set up and run a single-node
Kubernetes cluster locally on your machine.

**Note**: Minikube is primarily used for development and testing purposes.

#### Q7. True or False: kubectl cannot be installed on macOS.

1. [ ] True
2. [x] False

#### Explanation:

`kubectl` can be installed and used on macOS.

`kubectl` is a command-line tool used to interact with Kubernetes clusters, regardless of the operating system. It is
available for multiple platforms, including macOS, Linux, and Windows.

If you have Homebrew package manager installed, you can simply run the following command to install kubectl:

```
brew install kubectl
```

#### Q8. The configuration file for kubectl is ______.

1. [ ] Program Files(x86)/config
2. [x] /.kube/config
3. [ ] /home/kubernetes/kubeconfig
4. [ ] Program Files/kube

#### Explanation:

The configuration file for kubectl is typically located at `~/.kube/config` in the user's home directory.

This file stores the configuration details for kubectl to connect to a Kubernetes cluster, including the cluster's API
server address, authentication credentials, and other settings.

#### Q9. The command minikube dashboard runs which application?

1. [x] Kubernetes web-based interface
2. [ ] Shuts down Kubernetes
3. [ ] Pod details
4. [ ] Application builds

#### Explanation:

The command `minikube dashboard` runs the Kubernetes web-based interface, also known as the Kubernetes Dashboard. It
opens a browser window or tab and automatically redirects you to the locally running Kubernetes Dashboard.

The Kubernetes Dashboard provides a graphical user interface (GUI) for managing and monitoring your Minikube cluster. It
allows you to visualize and interact with various Kubernetes resources, such as pods, deployments, services, and more,
using an intuitive web interface.

#### Q10. Applications can be deployed to Kubernetes using all of these EXCEPT _______ .

1. [ ] kubectl command line
2. [ ] Kubernetes dashboard
3. [x] Docker
4. [ ] Yaml scripts

#### Explanation:

Docker is not used to directly deploy applications to Kubernetes. Docker is a containerization platform that allows you
to package applications and their dependencies into containers.

Kubernetes, on the other hand, is an orchestration platform that manages and scales containerized applications.

While Docker can be used to build container images that can be deployed to Kubernetes, it is not the primary tool used
for deploying applications to a Kubernetes cluster. Instead, you would typically use tools like `kubectl` command line,
Kubernetes dashboard, or Yaml scripts to deploy applications to Kubernetes.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 3.1

#### Kubernetes Hosted Configurations

#### Q1. True or False: kops is the only method for installing Kubernetes on Amazon Web Services (AWS).

1. [x] True
2. [ ] False

#### Explanation:

True.

Kops, short for Kubernetes Operations, is a set of tools for installing, operating, and deleting Kubernetes clusters in
the cloud. A rolling upgrade of an older version of Kubernetes to a new version can also be performed. It also manages
the cluster add-ons. After the cluster is created, the usual kubectl CLI can be used to manage resources in the cluster.

#### Q2. What is the utility for installing Kubernetes on Azure

1. [x] AKS
2. [ ] dir
3. [ ] kops
4. [ ] kubeadm

#### Explanation:

The utility for installing Kubernetes on Azure is AKS (Azure Kubernetes Service). AKS is a managed Kubernetes service
provided by Microsoft Azure. It simplifies the process of deploying and managing Kubernetes clusters on Azure by
abstracting away the underlying infrastructure and providing automated scaling, monitoring, and maintenance of the
Kubernetes control plane.

#### Q3. The Google Cloud Platform provides which tool and console for Kubernetes?

1. [ ] az aks
2. [ ] AWS
3. [x] Kubernetes Engine
4. [ ] kubernetes.io

#### Explanation:

The Google Cloud Platform provides the tool and console called "Kubernetes Engine" for Kubernetes. Kubernetes Engine (
GKE) is a managed Kubernetes service offered by Google Cloud. It allows you to deploy, manage, and scale containerized
applications using Kubernetes on Google Cloud Platform.

#### Q4. Kubernetes can be configured in all the following configurations except ______ .

1. [ ] Single-Node Installation
2. [ ] Single-Node etcd, Multi-Master and Multi-Worker Installation
3. [ ] Multi-Node etcd, Multi-Master Node and Multi-Worker Node Installation
4. [x] Blockchain

#### Explanation:

Kubernetes can be configured in all the following configurations except "Blockchain."

The configurations mentioned are valid deployment options in Kubernetes:

1. **Single-Node Installation**: This configuration involves running a single Kubernetes node with a single master and
   worker components. It is typically used for development or testing scenarios where a full cluster is not required.
2. **Single-Node etcd, Multi-Master, and Multi-Worker Installation**: In this configuration, a single etcd node is used
   for data storage, and there are multiple master and worker nodes. It provides high availability for the control plane
   by having multiple master nodes.
3. **Multi-Node etcd, Multi-Master Node, and Multi-Worker Node Installation**: This configuration involves having
   multiple etcd nodes for data storage, multiple master nodes for high availability and load balancing, and multiple
   worker nodes for running application containers. It is a common configuration for production environments.

#### Q5. What is the best Kubernetes option for business continuity?

1. [x] High Availability (HA)
2. [ ] Cloud
3. [ ] Single node
4. [ ] Not supported

#### Explanation:

The best Kubernetes option for business continuity is "High Availability (HA)."

High availability refers to the ability of a system or service to remain operational and accessible even in the face of
failures or disruptions. In the context of Kubernetes, implementing high availability ensures that the Kubernetes
control plane and worker nodes are resilient to failures, providing continuous availability of applications.

To achieve high availability in Kubernetes, the following practices and features can be utilized:

1. **Multi-Master Setup**: Deploying multiple Kubernetes master nodes helps distribute the control plane components and
   provides redundancy. In case one master node fails, the other nodes can take over, ensuring the uninterrupted
   operation of the cluster.
2. **Node Redundancy**: Running multiple worker nodes across different availability zones or regions helps distribute
   the workload and provides fault tolerance. If one worker node becomes unavailable, the remaining nodes can handle the
   workload, maintaining business continuity.
3. **Replication and Scaling**: Utilizing Kubernetes' built-in features like replication controllers or deployment
   replicas allows applications to be replicated across multiple nodes. This redundancy ensures that if one pod or
   container fails, there are backups available to handle requests.
4. **Load Balancing**: Configuring load balancers in front of worker nodes ensures that traffic is distributed evenly
   and can be redirected to healthy nodes in case of failures.

By implementing high availability practices in Kubernetes, businesses can minimize downtime, maintain application
availability, and ensure business continuity even in the event of failures or disruptions.

#### Q6. True of False: Kubernetes can be installed on commercial Cloud providers such as Amazon and Azure.

1. [x] True
2. [ ] False

#### Explanation:

True.

Kubernetes can be installed on commercial cloud providers such as Amazon Web Services (AWS) and Microsoft Azure.

#### Q7. How many popular installation strategies are there for Kubernetes?

1. [ ] 2
2. [x] 4
3. [ ] 6

#### Explanation:

There are multiple popular installation strategies for Kubernetes. The most common ones include:

1. **Self-Installation**: This involves manually setting up and configuring Kubernetes components on your own
   infrastructure or cloud provider by following the official Kubernetes documentation and installation guides.
2. **Kubernetes Distributions**: Various Kubernetes distributions, such as Rancher, OpenShift, and Charmed Kubernetes,
   provide pre-packaged installations of Kubernetes with additional features, management tools, and integrations.
3. **Managed Kubernetes Services**: Cloud providers like Amazon Web Services (AWS) with Amazon Elastic Kubernetes
   Service (EKS), Microsoft Azure with Azure Kubernetes Service (AKS), and Google Cloud Platform with Google Kubernetes
   Engine (GKE) offer managed Kubernetes services that handle the control plane, infrastructure management, and scaling
   for you.
4. **Kubernetes Installers**: Tools like `kops`, `kubeadm`, and `kubespray` provide automated installation and
   configuration options for Kubernetes clusters.

#### Q8. True or false? The Single Node Installation configuration is used only for production use cases.

1. [ ] True
2. [x] False

#### Explanation:

False. The Single Node Installation configuration is typically not used for production use cases.

The Single Node Installation configuration is primarily used for development, testing, or learning purposes where a
single-node Kubernetes cluster is sufficient. It allows individuals to run and experiment with Kubernetes on a single
machine without the need for a full-scale cluster. However, it lacks the resilience and fault tolerance required for
production environments.

In production scenarios, it is recommended to use multi-node configurations with multiple worker nodes and, optionally,
multiple master nodes to ensure high availability, scalability, and fault tolerance. These configurations distribute the
workload across multiple nodes and provide redundancy to handle failures or disruptions effectively.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 3.2

#### Hosted Deployments Scaling Updates and Rollbacks

#### Q1. The command to scale kubernetes deployment is?

1. [x] kubectl scale deployment
2. [ ] scale me
3. [ ] replica
4. [ ] kubectl get

#### Explanation:

The correct command to scale a Kubernetes deployment is:

```
kubectl scale deployment <deployment-name> --replicas=<number-of-replicas>
```

Replace `<deployment-name>` with the name of your deployment and `<number-of-replicas>` with the desired number of
replicas you want to scale to.

For example, if you have a deployment named "myapp" and you want to scale it to 3 replicas, the command would be:

```
kubectl scale deployment myapp --replicas=3
```

This command will adjust the number of replicas for the specified deployment, scaling it up or down.

#### Q2. True or False: the describe command returns details on Kubernetes items

1. [x] True
2. [ ] False

#### Explanation:

True.

The `describe` command is used to retrieve detailed information about various Kubernetes resources or items. It provides
a more comprehensive view of the specified resource, including its current state, configuration details, events, and
other relevant information.

#### Q3. The command kubectl rollout history returns what?

1. [ ] Nothing
2. [ ] Update data
3. [ ] Deployment listing
4. [x] Deployment revisions

#### Explanation:

The `kubectl rollout history` command in Kubernetes returns the revision history of a deployment. When a deployment is
updated, Kubernetes creates new revisions or versions of the deployment. Each revision represents a specific
configuration and state of the deployment.

By running `kubectl rollout history` followed by the deployment name, you can view the list of revisions for that
deployment. The command will display information such as the revision number, the timestamp of the revision, and whether
it was successfully rolled out.

#### Q4. The command kubectl set image deployment <deployment> <image name>=<image name>:<tag> –record, does what?

1. [ ] Returns status
2. [ ] nothing
3. [ ] Returns data
4. [x] Updates the deployment's current image

#### Q5. True or False: As `replicaset`s are updated, the previous revision of the replicaset is deleted.

1. [ ] True
2. [x] False

#### Explanation:

False.

In Kubernetes, as `replicaset`s are updated, the previous revision of the `replicaset` is not automatically deleted by
default.

`Replicaset`s are responsible for managing the desired number of replicas (pods) for a particular deployment.
When a deployment is updated, Kubernetes creates a new replicaset with the updated configuration while keeping the
previous replicaset active.

The reason for keeping the previous `replicaset` active is to ensure smooth and controlled rolling updates. Kubernetes
uses a rolling update strategy to gradually replace the old pods with new ones, ensuring that the application remains
available and stable throughout the update process. The previous `replicaset` continues to manage the old pods until the
new replicaset has successfully deployed and stabilized.

#### Q6. Which command rolls back a deployment?

1. [x] kubectl rollout undo deployment <deployment> --to-revision=<revision num>
2. [ ] None. It is not possible to rollback a deployment
3. [ ] rollout history
4. [ ] kubectl go back

#### Explanation:

By providing the `<deployment>` name and the `<revision num>` to which you want to roll back, Kubernetes will handle
scaling down the current replicas, scaling up the previous replicas, and updating the deployment to the desired
revision.

For example, if you have a deployment named "my-deployment" and you want to roll back to revision 3, the command would
be:

```
kubectl rollout undo deployment my-deployment --to-revision=3
```

#### Q7. True or False: If a revision is rolled back from revision 2, to revision 1, revision 1, gets renumbered to revision 3, which is the latest.

1. [x] True
2. [ ] False

#### Explanation:

False.

Revision 1 does become revision 3 when revision 2 is rolled back.

#### Q8. A _____ provides declarative updates for Pods and `Replicaset`s.

1. [ ] rollover
2. [x] deployment
3. [ ] controller

#### Explanation:

A deployment in Kubernetes provides declarative updates for Pods and `Replicaset`s. It is a higher-level resource that
allows you to define and manage the desired state of your application. Deployments abstract away the complexity of
managing individual Pods and `Replicaset`s and provide a convenient way to handle application deployments and updates.

Using a deployment, you can specify the desired number of replicas, the container image to use, environment variables,
volume mounts, and other configuration details. Kubernetes then takes care of managing the Pods and `Replicaset`s to
match the desired state defined by the deployment.

Here's an example of a Deployment manifest in Kubernetes:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-deployment
  labels:
    app: myapp
spec:
  replicas: 3
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
        - name: myapp-container
          image: myapp:latest
          ports:
            - containerPort: 8080

```

In this example, we define a Deployment named `myapp-deployment` with three replicas. The Deployment's selector ensures
that Pods managed by this Deployment have the label `app: myapp`.

Inside the Deployment's template, we define the desired Pod specification. The Pod template has a container named
`myapp-container` with an image specified as `myapp:latest`. It exposes port 8080 for incoming traffic.

By applying this Deployment manifest to a Kubernetes cluster, Kubernetes will create and manage three replicas of the
Pod template defined. If any changes are made to the Deployment, such as updating the image or scaling the number of
replicas, Kubernetes will handle the necessary rolling update or scaling operations to reach the desired state.

**Note**: in a real deployment, you may include additional configuration options, such as environment variables,
resource limits, or volume mounts, depending on the requirements of your application.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 4.1

#### Kublet Proxy Replicasets Daemonset and StatefulSets

#### Q1. A cluster in Kubernetes is ___________ .

1. [ ] replicas
2. [ ] a series of nodes
3. [ ] a special network
4. [x] a set of servers

#### Explanation:

In Kubernetes, a cluster is a set of servers (also known as nodes) that work together to run containerized applications
and manage their resources.

![k8s-cluster-components.png](..%2Fsrc%2Fkubernetes%2Fk8s-cluster-components.png)

These servers/nodes collectively form the underlying infrastructure for hosting and orchestrating containers. The
cluster consists of one or more master nodes that manage the overall control plane and one or more worker nodes that
execute and run the containers. Each node in the cluster contributes its resources and processing power to handle
containerized workloads efficiently.

**Note**: the correct answer is "a set of servers", but from my point of view "a series of nodes" is correct option too.

#### Q2. Which best describes a Kubernetes node?

1. [ ] A laptop
2. [ ] a Cloud of clusters
3. [x] Physical hardware and a virtual server that manages pods and containers
4. [ ] VMWare

#### Explanation:

A Kubernetes node refers to a physical or virtual machine within a cluster that runs containers.

A Kubernetes node consists of physical hardware, such as a server or virtual machine, and it hosts one or multiple pods.

#### Q3. True of False: A pod runs at least one container runtime.

1. [x] True
2. [ ] False

#### Explanation:

True.

A pod is the smallest unit of deployment in Kubernetes and represents a logical host for containers. It encapsulates one
or more containers and provides them with shared resources, such as network and storage. All containers within a pod
share the same network namespace and can communicate with each other via `localhost`. Therefore, a pod always includes
at least one container runtime responsible for running the containers within it.

![k8s-pods.svg](..%2Fsrc%2Fkubernetes%2Fk8s-pods.svg)

#### Q4. Another term for the master node is what

1. [ ] Container Node
2. [ ] Master cluster
3. [x] The api server
4. [ ] Runner

#### Explanation:

The master node in Kubernetes is responsible for managing and coordinating the cluster's overall operations.

The master node is also known as the control plane. One of the key components running on the master node is the API
server, which acts as the primary control and management point for the entire cluster.

![k8s-control-plane.png](..%2Fsrc%2Fkubernetes%2Fk8s-control-plane.png)

The API server exposes the Kubernetes API, allowing users and other components to interact with the cluster, perform
operations, and manage resources. Therefore, "The api server" is the appropriate term referring to the master node in
Kubernetes.

#### Q5. The etcd is _______ .

1. [ ] Network data
2. [ ] Backup information
3. [x] Storage for cluster management
4. [ ] Recycle bin

#### Explanation:

In Kubernetes, etcd is a distributed key-value store that serves as the primary storage for cluster management.

It is a reliable and consistent datastore that securely stores the configuration data of the cluster, including
information about the cluster's nodes, pods, services, configurations, and other important details. etcd ensures that
the cluster maintains a consistent state by providing a reliable source of truth for the cluster's data.

It plays a critical role in coordinating and synchronizing the activities of various components within the Kubernetes
cluster.

#### Q6. The kube-scheduler distributes processing to __________ .

1. [x] The containers in the worker nodes
2. [ ] Disk
3. [ ] External processing
4. [ ] The Master node

#### Explanation:

The kube-scheduler is a component of the Kubernetes control plane responsible for making scheduling decisions on where
to place pods within the cluster.

![k8s-control-plane.png](..%2Fsrc%2Fkubernetes%2Fk8s-control-plane.png)

The kube-scheduler examines the resource requirements and constraints of the pods and determines the most suitable
worker node on which to schedule them. The kube-scheduler considers factors such as available resources,
affinity/anti-affinity rules, node conditions, and other policies when making these decisions.

Once the kube-scheduler selects a worker node for a pod, the container runtime on that worker node is responsible for
managing and executing the containers within the pod. Therefore, the kube-scheduler distributes processing to the
containers running on the worker nodes, ensuring efficient resource utilization and workload distribution across the
cluster.

#### Q7. True or False: The kube-controller-manager detects failures in the nodes, pods, or containers.

1. [x] True
2. [ ] False

#### Explanation:

True. The kube-controller-manager in Kubernetes detects failures in the nodes, pods, or containers.

The kube-controller-manager is responsible for running various controllers that monitor the state of the cluster and
take actions to maintain the desired state.

These controllers include:

1. the Node Controller,
2. the Pod Controller,
3. the Replication Controller, among others.

They continuously monitor the cluster's components, such as nodes, pods, and containers, and detect any failures or
deviations from the desired state. Once a failure is detected, the kube-controller-manager takes
corrective actions, such as rescheduling pods, restarting containers, or scaling resources, to ensure the cluster
operates as intended.

Therefore, the kube-controller-manager plays a crucial role in detecting failures and maintaining
the desired state of the cluster.

#### Q8. The kubelet monitors pods to ensure ________ .

1. [ ] They are secure
2. [ ] There are pods.
3. [x] They are running
4. [ ] There are copies

#### Explanation:

The kubelet is a component that runs on each worker node in a Kubernetes cluster and its primary responsibility is to
manage the lifecycle of pods on its assigned node.

![k8s-cluster.png](..%2Fsrc%2Fkubernetes%2Fk8s-cluster.png)

The kubelet continuously monitors the state of pods assigned to it and takes actions to ensure that the pods are running
as expected. It communicates with the control plane, receives instructions on which pods to run, and makes sure they are
in the desired state.

The kubelet monitors pod health, restarts failed or unhealthy pods, and reports the status of the pods to the control
plane. It also takes care of pulling the required container images, setting up the networking, and managing the
resources for the pods.

Therefore, the kubelet's main role is to ensure that pods are running and maintain their desired
state within the Kubernetes cluster.

#### Q9. True or False: The kube-proxy does not manage a node's network connections.

1. [ ] True
2. [x] False

#### Explanation:

False. The kube-proxy does manage a node's network connections.

The kube-proxy is a component of the Kubernetes networking stack that runs on each worker node in a cluster. Its primary
responsibility is to manage network communication between services or pods within the cluster. It helps facilitate the
networking features provided by Kubernetes, such as load balancing, service discovery, and network routing.

The kube-proxy implements network proxying and forwarding rules to enable connectivity between different pods and
services. It sets up and manages network connections, such as IP tables rules or IPVS configurations, to ensure that the
desired network traffic is properly routed and load balanced.

#### Q10. Kubernetes administrators do all except _________ .

1. [ ] Validate hardware requirements, and the enterprise requirements
2. [x] Configure the database
3. [ ] Install nodes and design the pods and container strategy, including the implementation of selectors and labels.
4. [ ] Design the server, node, and high availability patterns

#### Explanation:

Kubernetes' administrators are primarily responsible for managing and orchestrating containerized applications within a
Kubernetes cluster. While they handle various tasks, including validating hardware requirements and enterprise
requirements, designing pods and container strategies, and implementing selectors and labels, configuring the database
is typically not part of their role. Database configuration is typically handled by database administrators or
specialized teams responsible for database management.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 4.2

<a id="module-4-2"></a>
#### PV, PVC, CSI and Authentication and Authorization

#### Q1. Persistent Volumes maintain _________ .

1. [x] Pod and other cluster Data
2. [ ] Nothing at all
3. [ ] Documentation
4. [ ] Containers

#### Explanation:

Persistent Volumes are a crucial component in Kubernetes that provide durable storage resources for applications running
within pods.

Persistent Volumes serve as an abstraction layer between the underlying storage infrastructure and the containers within
a cluster. PVs are designed to persist data even when pods are terminated, rescheduled, or deleted, ensuring data
availability and durability.

Here's an example of how Persistent Volumes (PVs) can be used in a Kubernetes cluster:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: example-pv
spec:
  capacity:
    storage: 10Gi
  accessModes:
    - ReadWriteOnce
  persistentVolumeReclaimPolicy: Retain
  storageClassName: standard
  hostPath:
    path: /data/example
```

In this example, we create a PV named "example-pv" with a capacity of 10 gigabytes (10Gi). It has the access mode set
to "ReadWriteOnce," which means it can be mounted by a single node at a time. The persistentVolumeReclaimPolicy is set
to "Retain," indicating that the PV should not be automatically deleted when released. The storageClassName is set to "
standard" to associate it with a particular storage class. The PV is configured with a hostPath, which represents a
directory on the host machine where the data will be stored.

#### Q2. True or False: A PersistentVolumeClaim is a request for storage issued by a user.

1. [x] True
2. [ ] False

#### Explanation:

True.

A PersistentVolumeClaim (PVC) is a request for storage issued by a user. A PVC is created by a user or an administrator
to request a specific amount and type of storage from a cluster's available PersistentVolumes (PVs). Once a PVC is
created, the Kubernetes cluster attempts to find and bind it to an appropriate PV that matches the specified criteria,
such as access mode, storage capacity, and storage class.

![k8s-pv-pvc.png](..%2Fsrc%2Fkubernetes%2Fk8s-pv-pvc.png)

Here's an example of how a PersistentVolumeClaim (PVC) is used as a request for storage in Kubernetes:

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: my-pvc
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
```

#### Q3. Which of the following is NOT true about the container storage interface (CSI)?

1. [ ] Installing new volume plugins
2. [x] Adding Pods
3. [ ] A standard developed to solve problems with adding new storage systems
4. [ ] Standards for exposing the container orchestration system to storage systems for their system payloads

#### Explanation:

Adding Pods is NOT true about the container storage interface (CSI).

The Container Storage Interface (CSI) is a standard developed to solve problems with adding new storage systems to
container orchestration platforms like Kubernetes. It defines a set of standards and specifications for exposing the
container orchestration system (e.g., Kubernetes) to storage systems, allowing them to be integrated as external volume
plugins.

CSI enables storage systems to expose their capabilities and features to containerized workloads running on the
orchestration platform.

Some key aspects of CSI include:

1. **Installing new volume plugins**: CSI allows for the installation and integration of new volume plugins into the
   container orchestration platform. These volume plugins provide access to specific storage systems and allow users to
   utilize various storage features and functionalities.
2. **Standards for exposing the container orchestration system to storage systems**: CSI defines a standard interface
   and communication protocol between the container orchestration system and storage systems. This enables storage
   systems to communicate with the orchestration platform, handle volume provisioning, mounting, and other storage
   operations.
3. **Standards for system payloads**: CSI specifies standards for the system payloads exchanged between the container
   orchestration platform and storage systems. This includes requests for volume creation, deletion, attachment,
   detachment, and other storage-related operations.

While CSI provides a standardized interface for storage systems and allows for the installation of new volume plugins,
it is not directly related to adding Pods. Pods are the fundamental units of deployment in Kubernetes and are
independent of the CSI specification.

#### Q4. Which is not a user type in Kubernetes?

1. [ ] Normal User
2. [ ] Service accounts
3. [x] Basic Users

#### Explanation:

Basic Users is not a user type in Kubernetes.

In Kubernetes, there are two primary user types:

**Normal User**:

A normal user is an individual user with authentication credentials who interacts with the Kubernetes cluster. Normal
users can perform various operations, such as creating and managing resources, deploying applications, and accessing
cluster information. They are typically authenticated using mechanisms like certificates, tokens, or external
authentication providers.

**Service Accounts**:

Service accounts are a specific type of user account intended for use by applications and services running within the
cluster. Service accounts are associated with Pods and provide an identity for the application or service to interact
with the Kubernetes API server and other resources. They are primarily used for authentication and authorization
purposes within the cluster.

#### Q5. Which is not a Kubernetes authorization module?

1. [x] LDAP Module
2. [ ] Attribute-Based Access Control (ABAC) Authorizer
3. [ ] Node Authorizer

#### Explanation:

LDAP Module is not a Kubernetes authorization module.

Kubernetes provides several authorization modules to control access to its resources. However, the LDAP module is not
one of them. LDAP (Lightweight Directory Access Protocol) is a protocol used for accessing and maintaining directory
services. While LDAP can be used for authentication purposes in Kubernetes, it is not specifically considered an
authorization module.

The two Kubernetes authorization modules mentioned in the options are:

**Attribute-Based Access Control (ABAC) Authorizer**:

ABAC is a basic authorization mechanism in Kubernetes where access decisions are made based on attributes associated
with the user, group, or request context. ABAC policies define rules that match on attributes and allow or deny access
based on those rules.

**Node Authorizer**:

The Node Authorizer is a component in Kubernetes responsible for authorizing `kubelet` (node) actions. It determines
what actions a node is allowed to perform, such as creating pods or updating node status. The Node Authorizer checks
against predefined policies to determine whether a `kubelet` is authorized to perform certain operations.

#### Q6. True or False: The Role-Based Access Control (RBAC) Authorizer acts like role based security

1. [x] True
2. [ ] False

#### Explanation:

True.

The Role-Based Access Control (RBAC) Authorizer in Kubernetes provides role-based security. RBAC allows you to define
roles and bind them to users or groups, granting specific permissions to perform actions on Kubernetes resources. It
provides a flexible and granular way to control access to various operations and resources within the cluster based on
roles and their associated permissions.

![k8s-rbac-diagram.png](..%2Fsrc%2Fkubernetes%2Fk8s-rbac-diagram.png)

Here's an example of using Role-Based Access Control (RBAC) in Kubernetes.

**1. Define a ServiceAccount**:

A ServiceAccount represents an identity for applications or services running within the cluster.

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
name: my-service-account
```

In this example, we create a ServiceAccount named "my-service-account" that represents an application or service running
within the cluster.

**2. Define a Role**:

A Role defines a set of permissions that can be granted to users or groups.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
name: my-role
rules:
  - apiGroups: [ "" ]
    resources: [ "pods" ]
    verbs: [ "get", "list", "watch" ]
```

In this example, we define a Role named "my-role" that grants permissions to perform "get," "list," and "watch" actions
on "pods" resources.

**3. Create a RoleBinding**:

A RoleBinding associates a Role with a user, group, or ServiceAccount, granting them the permissions defined in the
Role.

```yaml
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: my-role-binding
subjects:
  - kind: ServiceAccount
    name: my-service-account
    namespace: default
roleRef:
  kind: Role
  name: my-role
  apiGroup: rbac.authorization.k8s.io
```

In this example, we create a RoleBinding named "my-role-binding" that binds the Role "my-role" to the ServiceAccount "
my-service-account" in the default namespace. This means that the ServiceAccount "my-service-account" will have the
permissions defined in the Role "my-role" for the specified resources.

By associating a ServiceAccount with a Role using a RoleBinding, you can grant specific permissions to applications or
services running within the cluster, allowing them to access and interact with resources based on the defined Role's
permissions.

#### Q7. Admission control is used to specify all the following except  _______ .

1. [ ] Granular access control policies
2. [x] Open Source access
3. [ ] To use admission controls

#### Explanation:

Open Source access is not a purpose of using admission control in Kubernetes.

Admission control in Kubernetes is a feature that allows administrators to define and enforce certain policies and rules
before objects are created, modified, or deleted in the cluster. It acts as a gatekeeper, validating and mutating
requests to ensure they comply with predefined rules.

The primary purposes of using admission control are:

**Granular access control policies**:

Admission control enables administrators to enforce fine-grained access control policies. It can be used to restrict
certain actions or configurations, such as preventing privileged containers, enforcing resource quotas, or validating
pod specifications.

**To use admission controls**:

The main purpose of admission control is to apply a set of predefined checks and validations on incoming requests to
ensure compliance with desired policies. Admission control can include validating object configurations, checking
resource constraints, or applying default values.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>
