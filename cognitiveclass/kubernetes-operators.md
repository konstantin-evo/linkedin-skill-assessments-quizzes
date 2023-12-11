## Kubernetes Operators

[Link to course](https://apps.cognitiveclass.ai/learning/course/course-v1:IBM+CO0302EN+v1/home)

<a name="link-top"></a>

---

### Table of Contents

<ol>
  <li>
    <a href="#module-1">Module 1 - Reconciliation Loops</a>
  </li>
  <li>
    <a href="#module-2">Module 2 - Operator Lifecycle Manager</a>
  </li>
  <li>
    <a href="#module-3">Module 3 - Scorecard</a>
  </li>
  <li>
    <a href="#final-exam">Final Exam</a>
  </li>
</ol>

---

#### Module 1

#### Reconciliation Loops

#### Practice Question 1

**Users interact with a Kubernetes cluster by issuing commands to controllers to create resources.**

1. [ ] True
2. [x] False

#### Explanation:

In Kubernetes, users typically interact with a cluster using the kubectl command-line tool or other Kubernetes API
clients. While controllers are an essential part of Kubernetes and play a role in managing the desired state of
resources, users don't directly issue commands to controllers. Instead, they define the desired state of the cluster by
creating resource manifests (YAML or JSON files) and then use kubectl apply or similar commands to apply those manifests
to the cluster.

#### Practice Question 2

**What is the first thing you should always do when entering a reconciliation loop?**

1. [ ] Exit and requeue the request
2. [x] Fetch the object you're reconciling
3. [ ] Start iterating on reconciling the object
4. [ ] Check for errors in the reconciliation request unanswered

#### Explanation:

When entering a reconciliation loop in a Kubernetes controller, the first step is typically to fetch the current state
of the object that needs to be reconciled. This ensures that the controller has the most up-to-date information about
the object before proceeding with any reconciliation logic.

#### Practice Question 3

**Many controllers are often involved in the reconciliation of a single object.**

1. [x] True
2. [ ] False

#### Explanation:

In Kubernetes, it's common for multiple controllers to be involved in the reconciliation of a single object. Each
controller is responsible for managing specific aspects or resources associated with an object. This concept is known
as "control loops" or "controllers working together."

For example, consider a scenario where you have a custom resource that is managed by different controllers. One
controller might be responsible for handling networking aspects, another for storage, and another for security. These
controllers work together to ensure that the overall desired state of the custom resource is achieved.

#### Review Question 1

**What are the results that can be returned from a single iteration of a reconcile loop?**

1. [ ] Requeue, Exit without requeuing
2. [x] Return and requeue, Return an error and requeue, Exit without requeuing
3. [ ] Exit, Exit with error
4. [ ] Return and requeue, Return an error, Exit without requeuing

#### Explanation:

In a reconciliation loop, after processing the current iteration, you may decide to return and requeue the request for
further reconciliation, return an error and requeue if there was an issue that might be resolved later, or exit without
requeuing if the reconciliation was successful or there's no need to retry.

#### Review Question 2

**The reconciliation loop is where the actual behavior of an operator is defined.**

1. [x] True
2. [ ] False

#### Explanation:

The reconciliation loop is a central component of a Kubernetes operator and is where much of the operator's control
logic and behavior are implemented.

However, it's important to note that the overall behavior of an operator is not limited to the reconciliation loop
alone. The operator's behavior is indeed defined by its code, which includes not only the reconciliation logic but also
other components such as event handling, resource management, and interactions with the Kubernetes API.

#### Review Question 3

**Why is it a good idea to build a reconciliation loop out of small, iterative steps?**

1. [ ] The desired state of the cluster can change during reconciliation
2. [ ] The actual state of the cluster can change during reconciliation
3. [ ] The reconciliation request might be picked up by multiple controllers
4. [x] All of the above

#### Explanation:

Building the reconciliation loop with small, iterative steps helps to accommodate changes in the desired or actual state
of the cluster during reconciliation. It also helps handle scenarios where multiple controllers might be working on the
same object, ensuring a more resilient and adaptive reconciliation process.

#### Review Question 4

**What do the Kube-builder markers we put above the Reconcile method declaration do?**

1. [ ] The reconciliation request might be picked up by multiple controllers
2. [x] Create the RBAC for the controller to access the specified resources
3. [ ] Scaffold the custom resource types for the operator
4. [ ] Scaffold the reconcile loops for the specified resources

#### Explanation:

Kube-builder relies on the controller-gen tool to generate various artifacts like RBAC (Role-Based Access Control)
manifests. Annotations are often used in the comments of the code to guide the controller-gen tool on how to generate
these artifacts.

For example, you might see comments like the following above your Reconcile method declaration:

```
// +kubebuilder:rbac:groups=mygroup,resources=myresources,verbs=get;list;watch;create;update;patch;delete
```

This annotation tells controller-gen to generate RBAC rules that grant the necessary permissions for the controller to
perform operations (get, list, watch, create, update, patch, delete) on resources of the specified API group and
resource type.

#### Review Question 5

**It is possible for the object you are reconciling to no longer exist by the time the request is being processed.**

1. [x] True
2. [ ] False

#### Explanation:

Yes, it is possible for the object being reconciled to no longer exist by the time the reconciliation request is being
processed. This is an important consideration when designing controllers, and operators need to handle such scenarios
gracefully, possibly by checking for the existence of the object before attempting any operations on it.

---

#### Module 2

#### Operator Lifecycle Manager

#### Practice Question 1

**Operator developers are expected to understand how OLM works to install their own operator bundles.**

- [ ] True
- [x] False

#### Explanation

Operator developers are not necessarily required to understand how OLM (Operator Lifecycle Manager) works; OLM is
responsible for installing and managing operators, and developers typically focus on creating the operator itself.

---

### Practice Question 2

**What information is contained in the bundle's manifests?**

- [ ] Kubernetes yaml files for installing OLM
- [x] Kubernetes yaml files that contain the resources that make up the operator
- [ ] Manifests for creating the operator container image
- [ ] Manifests for creating the bundle container image

#### Explanation

The bundle's manifests include Kubernetes yaml files that define the resources making up the operator,
such as CustomResourceDefinitions (CRDs) and other necessary components.

---

### Practice Question 3

**Multiple API versions of a resource can exist in a cluster simultaneously.**

- [x] True
- [ ] False

#### Explanation

In Kubernetes, multiple API versions of a resource can coexist in a cluster simultaneously. This allows
for gradual updates and compatibility with different versions of controllers or clients.

---

### Review Question 1

**What are the three main components of a bundle?**

1. [ ] Sample, Config, and Image
2. [x] Manifests, Metadata, and a Dockerfile
3. [ ] Config, an Operator image, and a bundle image
4. [ ] Data, Metadata, and a Dockerfile

#### Explanation

A bundle is a package that includes all the necessary components and metadata required to deploy and manage an operator.
This might include Kubernetes Custom Resource Definitions (CRDs), RBAC (Role-Based Access Control) configurations,
service accounts, deployment descriptors, and other resources.

A bundle typically consists of:

1. Manifests (Kubernetes yaml files defining resources),
2. Metadata (information about the bundle),
3. A Dockerfile (specifying how to build the operator image).

---

### Review Question 2

**A conversion webhook is a special kind of admission webhook.**

- [x] True
- [ ] False

#### Explanation

A conversion webhook is a specific type of admission webhook used for converting
resources between different versions. It plays a role in ensuring compatibility during API version upgrades.

---

### Review Question 3

**Why is it important to include a conversion webhook when upgrading the API version of an operator?**

1. [ ] To convert running instances to the new version of Memcached
2. [x] To migrate requests from users and controllers to the new version
3. [ ] To migrate the database records to the new version
4. [ ] To convert pre-existing instances of the resource to the new version

#### Explanation

When upgrading the API version of an operator, a conversion webhook is essential to handle the transition of requests
from users and controllers to the new version seamlessly.

This ensures that existing requests and configurations are correctly interpreted and processed by the updated API
version. While the conversion webhook may also play a role in converting pre-existing instances of the resource (option
4), the primary purpose, especially during upgrades, is to manage the incoming requests effectively.

---

### Review Question 4

**Kubernetes' conversion logic is based on what kind of model?**

1. [ ] Many to Many
2. [x] Hub and Spoke
3. [ ] Up and Down
4. [ ] Wheel and Deal

#### Explanation

Since we now have two different versions, and users can request either version, we’ll have to define a way to convert
between our version. For CRDs, this is done using a webhook, similar to the defaulting and validating webhooks. Like
before, controller-runtime will help us wire together the nitty-gritty bits, we just have to implement the actual
conversion.

A simple approach to defining conversion might be to define conversion functions to convert between each of our
versions. Then, whenever we need to convert, we’d look up the appropriate function, and call it to run the conversion.

This works fine when we just have two versions, but what if we had 4 types? 8 types? That’d be a lot of conversion
functions.

Instead, controller-runtime models conversion in terms of a “hub and spoke” model – we mark one version as the “hub”,
and all other versions just define conversion to and from the hub:

<div style="text-align: center;">
  <img src="../src/kubernetes-operators/hub-and-spoke.png" alt="hub and spoke" style="width: 30%;">
</div>

Then, if we have to convert between two non-hub versions, we first convert to the hub version, and then to our desired
version:

<div style="text-align: center;">
  <img src="../src/kubernetes-operators/conversion-logic.png" alt="conversion logic" style="width: 30%;">
</div>

This cuts down on the number of conversion functions that we have to define, and is modeled off of what Kubernetes does
internally.

---

### Review Question 5

**Although the underlying custom resources that OLM uses may change, the format of an operator bundle should stay the
same moving forward.**

- [x] True
- [ ] False

#### Explanation

While the custom resources (CRs) used by the Operator Lifecycle Manager may undergo changes, the format of an
operator bundle should remain consistent in the future. This is typically true due to several reasons:

1. **Compatibility:** Maintaining a consistent format for operator bundles ensures backward compatibility. Applications
   and systems that rely on these bundles can continue to work seamlessly even as the underlying custom resources
   evolve.

2. **Interoperability:** A consistent format promotes interoperability between different versions of the Operator
   Lifecycle Manager. Operators are designed to work within specific environments, and having a stable bundle format
   helps ensure that operators developed for a particular version of OLM can still be used with future versions.

3. **Developer Experience:** Developers who create operators and bundles benefit from a stable format. It allows them to
   focus on improving the functionality of their operators without constantly adjusting to changes in the bundle
   structure.

4. **Upgradability:** With a consistent format, the upgrade process for operators becomes smoother. If the bundle format
   remains the same, upgrading an operator doesn't require extensive modifications to the operator bundle itself,
   simplifying the update process.

---

#### Module 3

#### Scorecard

#### Practice Question 1

**Custom Scorecard test suites are provided as container images.**

1. [x] True
2. [ ] False

#### Explanation

While the Operator SDK bundle validate subcommand can validate local bundle directories and remote bundle images for
content and structure, you can use the scorecard command to run tests on your Operator based on a configuration file and
test images. These tests are implemented within test images that are configured and constructed to be executed by the
scorecard.

Link: [Validating Operators using the scorecard tool](https://docs.openshift.com/container-platform/4.8/operators/operator_sdk/osdk-scorecard.html)

---

#### Practice Question 2

**Your bundle starts with some automatically generated Scorecard tests that test what features of your operator?**

1. [ ] Regression tests to test upgrading your operator
2. [x] Basic best practices like descriptors and validators for your custom resource types
3. [ ] Benchmarks to stress-test your operator
4. [ ] Basic unit tests that test your custom resource types

#### Explanation

When your bundle starts with automatically generated Scorecard tests, these tests are designed to assess fundamental
aspects of your operator's implementation and adherence to best practices. Specifically, they focus on:

These tests examine whether your operator follows recommended practices, such as using appropriate descriptors and
validators for your custom resource types. This ensures that your operator aligns with established conventions and
guidelines.

---

#### Practice Question 3

**Custom Scorecard test suites can contain multiple tests.**

1. [x] True
2. [ ] False

#### Explanation

Custom Scorecard test suites can indeed contain multiple tests to evaluate various aspects of your operator.

---

#### Review Questions 1

**In the config file, each Scorecard test consists of what three components?**

1. [ ] Operator image, Test image, Test command
2. [x] Image, Entrypoint, Labels
3. [ ] Test file, Commands, Bundle
4. [ ] Dockerfile, Entrypoint, Name

#### Explanation

Scorecard test consists of the following components:

1. **Image:** This component refers to the container image that contains the Scorecard test. It specifies the
   environment in which the test will be executed.
2. **Entrypoint:** The entrypoint is the command or script that will be executed when the container starts. It defines
   how the Scorecard test should be run within the container.
3. **Labels:** Labels are metadata that can be associated with the Scorecard test. They provide additional information
   about the test, such as its purpose or any specific requirements.

These three components collectively define the configuration of a Scorecard test within the configuration file. The
image determines the environment, the entrypoint specifies how the test should be executed, and labels provide
additional context or information.

---

#### Review Questions 2

**Scorecard tests execute from your local machine targeting the cluster.**

1. [ ] True
2. [x] False

#### Explanation

Scorecard tests are executed within a container on the cluster, not from your local machine.

---

#### Review Questions 3

**Why did we have to cross-compile our Scorecard test?**

1. [ ] To include our Scorecard config
2. [x] It’s executed in a container on the cluster, which is a 64-bit Linux environment
3. [ ] To include our operator’s bundle
4. [ ] To ensure all the dependencies were included

#### Explanation

Cross-compilation refers to the process of compiling code on one platform (architecture or operating system) to run on a
different platform.

In the context of the Scorecard test, the need for cross-compilation arises because the test is executed within a
container on the Kubernetes cluster, and this cluster typically operates in a 64-bit Linux environment.

---

#### Review Questions 4

**Why did we run our Scorecard test with our operator’s Service Account?**

1. [ ] To give Scorecard the RBAC permissions to run the test container
2. [x] To give it the RBAC permissions needed to manipulate the Memcached and dependent types
3. [ ] To give it the RBAC permissions to manipulate our operator’s controller
4. [ ] To tell it which operator to test

#### Explanation

The Scorecard test may need to interact with resources such as Memcached or other dependent types during the evaluation.
Running the test with the operator’s Service Account ensures that it has the necessary RBAC permissions to perform these
interactions.

---

#### Review Questions 5

**The Scorecard config is part of your operator’s bundle.**

1. [x] True
2. [ ] False

#### Explanation

The scorecard tool uses a configuration that allows you to configure internal plugins, as well as several global
configuration options. Tests are driven by a configuration file named config.yaml, which is generated by the make bundle
command, located in your `bundle/` directory:

```
./bundle
...
└── tests
    └── scorecard
        └── config.yaml
```

Example scorecard configuration file:

```yaml
kind: Configuration
apiversion: scorecard.operatorframework.io/v1alpha3
metadata:
  name: config
stages:
  - parallel: true
    tests:
      - image: quay.io/operator-framework/scorecard-test:v1.8.0
        entrypoint:
          - scorecard-test
          - basic-check-spec
        labels:
          suite: basic
          test: basic-check-spec-test
      - image: quay.io/operator-framework/scorecard-test:v1.8.0
        entrypoint:
          - scorecard-test
          - olm-bundle-validation
        labels:
          suite: olm
          test: olm-bundle-validation-test
```

Link: [Scorecard configuration](https://docs.openshift.com/container-platform/4.8/operators/operator_sdk/osdk-scorecard.html#osdk-scorecard-config_osdk-scorecard)

---

#### Final Exam

#### Question 1

**Your Scorecard config is automatically generated as part of your operator’s bundle.**

1. [x] True
2. [ ] False

#### Explanation

A default set of Kustomize files are generated by the Operator SDK after running the `init` command. The default
`bundle/tests/scorecard/config.yaml` file that is generated can be immediately used to run the scorecard tool against
your Operator, or you can modify this file to your test specifications.

Example of `config.yaml`:

```yaml
apiVersion: scorecard.operatorframework.io/v1alpha3
kind: Configuration
metadata:
  name: config
stages:
  - parallel: true
    tests:
      - entrypoint:
          - scorecard-test
          - basic-check-spec
        image: quay.io/operator-framework/scorecard-test:v1.32.0
        labels:
          suite: basic
          test: basic-check-spec-test
        storage:
          spec:
            mountPath: { }
      - entrypoint:
          - scorecard-test
          - olm-bundle-validation
        image: quay.io/operator-framework/scorecard-test:v1.32.0
        labels:
          suite: olm
          test: olm-bundle-validation-test
        storage:
          spec:
            mountPath: { }
      - entrypoint:
          - scorecard-test
          - olm-crds-have-validation
        image: quay.io/operator-framework/scorecard-test:v1.32.0
        labels:
          suite: olm
          test: olm-crds-have-validation-test
        storage:
          spec:
            mountPath: { }
      - entrypoint:
          - scorecard-test
          - olm-crds-have-resources
        image: quay.io/operator-framework/scorecard-test:v1.32.0
        labels:
          suite: olm
          test: olm-crds-have-resources-test
        storage:
          spec:
            mountPath: { }
      - entrypoint:
          - scorecard-test
          - olm-spec-descriptors
        image: quay.io/operator-framework/scorecard-test:v1.32.0
        labels:
          suite: olm
          test: olm-spec-descriptors-test
        storage:
          spec:
            mountPath: { }
      - entrypoint:
          - scorecard-test
          - olm-status-descriptors
        image: quay.io/operator-framework/scorecard-test:v1.32.0
        labels:
          suite: olm
          test: olm-status-descriptors-test
        storage:
          spec:
            mountPath: { }
storage:
  spec:
    mountPath: { }
```

---

#### Question 2

**Why is it important to include a conversion webhook when upgrading the API version of an operator?**

1. [ ] To convert running instances to the new version of Memcached
2. [x] To migrate requests from users and controllers to the new version
3. [ ] To migrate the database records to the new version
4. [ ] To convert pre-existing instances of the resource to the new version

#### Explanation

The conversion webhook facilitates the transformation of incoming requests made by users and controllers to the new API
version. It ensures that the requests conform to the updated structure and schema of the new version, allowing for a
smooth transition without breaking existing functionality.

---

#### Question 3

**Your bundle starts with some automatically generated Scorecard tests that test what features of your operator?**

1. [ ] Regression tests to test upgrading your operator
2. [x] Basic best practices like descriptors and validators for your custom resource types
3. [ ] Benchmarks to stress-test your operator
4. [ ] Basic unit tests that test your custom resource types

#### Explanation

The automatically generated Scorecard tests for your bundle focus on basic best practices, such as descriptors and
validators for your custom resource types.

---

#### Question 4

**What are the results that can be returned from a single iteration of a reconcile loop?**

1. [ ] Requeue, Exit without requeuing
2. [x] Return and requeue, Return an error and requeue, Exit without requeuing
3. [ ] Exit, Exit with error
4. [ ] Return and requeue, Return an error, Exit without requeuing

#### Explanation:

In a reconciliation loop, after processing the current iteration, you may decide to return and requeue the request for
further reconciliation, return an error and requeue if there was an issue that might be resolved later, or exit without
requeuing if the reconciliation was successful or there's no need to retry.

---

#### Question 5

**Conversion between different API versions of the same resource is based on a Hub-and-Spoke model.**

1. [x] True
2. [ ] False

#### Explanation

controller-runtime models conversion in terms of a “hub and spoke” model – we mark one version as the “hub”,
and all other versions just define conversion to and from the hub:

<div style="text-align: center;">
  <img src="../src/kubernetes-operators/hub-and-spoke.png" alt="hub and spoke" style="width: 30%;">
</div>

Then, if we have to convert between two non-hub versions, we first convert to the hub version, and then to our desired
version:

<div style="text-align: center;">
  <img src="../src/kubernetes-operators/conversion-logic.png" alt="conversion logic" style="width: 30%;">
</div>

This cuts down on the number of conversion functions that we have to define, and is modeled off of what Kubernetes does
internally.

---

#### Question 6

**Why should you start a reconciliation loop by fetching the object you’re reconciling?**

1. [ ] To get the most recent API version of the object
2. [x] The object may have been deleted, updated, or otherwise invalidated in the meantime
3. [ ] To fetch the object’s schema
4. [ ] The object isn’t included in the reconciliation request

#### Explanation

One of the primary reasons for fetching the object is to account for changes that might have occurred since the last
reconciliation iteration. The object may have been deleted, updated, or invalidated by external factors, and fetching it
allows the operator to reconcile based on the most recent state.

---

#### Question 7

**A conversion webhook is a special type of which kind of default Kubernetes resource?**

1. [ ] Controller webhook
2. [x] Mutating webhook
3. [ ] Upgrade webhook
4. [ ] Admission webhook

#### Explanation

In Kubernetes, a mutating webhook is a special type of admission webhook. Admission webhooks are HTTP callbacks that
receive admission requests and do something with them. They can be used to intercept and potentially modify admission
requests to the Kubernetes API server.

A mutating webhook, specifically, is designed to modify the objects being admitted. It allows you to intercept an
admission request, make changes to the object being created or updated, and then admit the modified object to the
Kubernetes API server. This provides a way to dynamically mutate resources before they are persisted in the cluster.

---

#### Question 8

**Why is it a good idea to build a reconciliation loop out of small, iterative steps?**

1. [ ] The desired state of the cluster can change during reconciliation
2. [ ] The actual state of the cluster can change during reconciliation
3. [ ] The reconciliation request might be picked up by multiple controllers
4. [x] All of the above

#### Explanation

Building a reconciliation loop out of small, iterative steps is a good idea because all the mentioned options are true.
The desired state, actual state, and the possibility of multiple controllers handling the reconciliation request are
factors to consider.

---

#### Question 9

**What are the three main components of a bundle?**

1. [ ] Sample, Config, and Image
2. [x] Manifests, Metadata, and a Dockerfile
3. [ ] Config, an Operator image, and a bundle image
4. [ ] Data, Metadata, and a Dockerfile

#### Explanation

A bundle is a package that includes all the necessary components and metadata required to deploy and manage an operator.
This might include Kubernetes Custom Resource Definitions (CRDs), RBAC (Role-Based Access Control) configurations,
service accounts, deployment descriptors, and other resources.

A bundle typically consists of:

1. Manifests (Kubernetes yaml files defining resources),
2. Metadata (information about the bundle),
3. A Dockerfile (specifying how to build the operator image).

---

#### Question 10

**A Scorecard test requires a Service Account with permissions to access your custom resource types.**

1. [x] True
2. [ ] False

#### Explanation

A Scorecard test requires a Service Account with permissions to access your custom resource types to evaluate and test
your Kubernetes operator.
