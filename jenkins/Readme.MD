Created a NS : POC

sass273491@ROL00120:~/poc/poc/jenkins$ k get namespace | grep -i poc
poc                    Active   16m

Pull helm charts
------------------

$ helm repo add jenkinsci https://charts.jenkins.io
$ helm repo update
$ helm search repo jenkinsci

Storage
-------

Create a peristance storage

Then change ownership of the data share "/home/sass273491/data"

minikube ssh
chown 1000:1000 /home/sass273491/data

Create a service account
-------------------------

In Kubernetes, service accounts are used to provide an identity for pods. Pods that want to interact with the API server will authenticate with a particular service account. By default, applications will authenticate as the default service account in the namespace they are running in. This means, for example, that an application running in the test namespace will use the default service account of the test namespace.

We will create a service account called poc:

A ClusterRole is a set of permissions that can be assigned to resources within a given cluster. Kubernetes APIs are categorized into API groups, based on the API objects that they relate to. While creating a ClusterRole, you can specify the operations that can be performed by the ClusterRole on one or more API objects in one or more API groups, just as we have done above. ClusterRoles have several uses. You can use a ClusterRole to:

define permissions on namespaced resources and be granted within individual namespace(s)

define permissions on namespaced resources and be granted across all namespaces

define permissions on cluster-scoped resources

If you want to define a role cluster-wide, use a ClusterRole; if you want to define a role within a namespace, use a Role.

A role binding grants the permissions defined in a role to a user or set of users. It holds a list of subjects (users, groups, or service accounts), and a reference to the role being granted.

A RoleBinding may reference any Role in the same namespace. Alternatively, a RoleBinding can reference a ClusterRole and bind that ClusterRole to the namespace of the RoleBinding. To bind a ClusterRole to all the namespaces in our cluster, we use a ClusterRoleBinding.

---




bf7f06bfb6bc4cb88c38f93aa03f4202