# Chapter 2. Kubernetes API Basics

## Notes

A **resource** is an endpoint in the K8s API that stores a collection of API objects of a certain Kind.

In this example, the resource is pod.

/apis/batch/v1/namespaces/mynamespace/**pod**



API **objects** are persistent entities in the Kubernetes system.

In this example, the objects are bestie-application-deployment-7867cdd587-w8cjb, and mysql-5554d8b57b-mrznr.

\----------------------

oc get pods                               &#x20;

NAME                                             READY   STATUS    RESTARTS   AGE                                                                             &#x20;

bestie-application-deployment-7867cdd587-w8cjb   1/1     Running   0          17m                                                                             &#x20;

mysql-5554d8b57b-mrznr                           1/1     Running   0          17m                &#x20;

****

**Kind** is the type of entity.

In the example above, the kind for the object, bestie-application-deployment-7867cdd587-w8cjb,  is Pod.

## FAQ

What is kubectl proxy ?

This command proxies the Kubernetes API to our local machine and also takes care of the authentication and authorization bits. It allows us to directly issue requests via HTTP and receive JSON payloads in return.

