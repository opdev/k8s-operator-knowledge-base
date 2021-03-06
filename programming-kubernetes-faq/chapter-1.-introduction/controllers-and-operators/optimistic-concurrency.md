# Optimistic Concurrency

## Notes

**Optimistic concurrency** - If and when the API server detects concurrent write attempts, it rejects the latter of the two write operations. It is then up to the client to handle a conflict and potentially retry the write operation.

Conflict errors are totally normal in controllers. Always expect them and handle them gracefully.

Optimistic concurrency is a perfect fit for level-based logic, because by using level-based logic you can just rerun the control loop. Another run of that loop will automatically undo optimistic changes from the previous failed optimistic attempt, and it will try to update the world to the latest state.

**Optimistic concurrency control (OCC)** - It assumes that concurrent transactions of multiple users will not affect each other during processing, and each transaction can process its own data without requesting a lock. Before committing the data update, each transaction will first check whether other transactions have modified the data after the transaction reads the data. If other transactions are updated, the transaction that is being committed will be rolled back.

{% embed url="https://docs.microsoft.com/en-us/dotnet/framework/data/adonet/optimistic-concurrency" %}

## FAQ

**How does optimistic concurrency work in Kubernetes ?**

Kubernetes uses the Optimistic Concurrency Control or OCC. It is a method where the piece of data includes a version number. Every time the data is updated, the version number increases.

Example:

Imagine your client is not the only actor in the cluster that modifies a pod. There is “another actor, namely the kubelet, that constantly modifies some fields because a container is constantly crashing. Now your controller reads the pod object’s latest state like so:&#x20;

kind: Pod&#x20;

metadata:&#x20;

&#x20;  name: foo&#x20;

&#x20;  resourceVersion: 57&#x20;

spec:&#x20;

&#x20;  ...&#x20;

status:&#x20;

&#x20;  ...&#x20;

Now assume the controller needs several seconds with its updates to the world. Seven seconds later, it tries to update the pod it read—for example, it sets an annotation. Meanwhile, the kubelet has noticed yet another container restart and updated the pod’s status to reflect that; that is, resourceVersion has increased to 58.&#x20;

The object your controller sends in the update request has resourceVersion: 57. The API server tries to set the etcd key for the pod with that value. etcd notices that the resource versions do not match and reports back that 57 conflicts with 58. The update fails.”
