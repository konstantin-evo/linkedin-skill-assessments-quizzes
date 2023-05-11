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
