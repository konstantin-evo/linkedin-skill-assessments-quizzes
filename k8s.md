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